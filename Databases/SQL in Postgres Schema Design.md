# SQL in Postgres Schema Design

## Primary Keys

### Overview

A primary key = `NOT NULL` + `UNIQUE` constraint.
Recall that a primary key can be natural and surrogate.
When a primary key is created, a B-tree index is created as well.

An example of primary key:

    id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY

`GENERATED ALWAYS AS IDENTITY` prohibits a manual ID insertion.

### UUID as a primary key

A UUID has the following advantages over a plain sequential id:

* UUID can be generated on a client:

      So you don't have to rely on a database sequencing.

* UUID simplifies data sharding:

      Since you can insert records into multiple shards
      without relying on a central sequencing authority.

## Normalization

Normalization allows you to reduce data redundancy within a table.
You usually consider the usage of 1NF, 2NF, 3NF.

## Foreign References

### What can a foreign key reference?

A foreign key must reference a primary key or a unique column.

### NOT NULL has to be explicit

Foreign key does not prohibit a `NULL` to be present.
If you want to enforce a reference to an external column, use the `NOT NULL` constraint.

### One-to-one references

One can implement one-to-one relation using `REFERENCES` with the `UNIQUE` constraint.

## Markers

Always add created_at, updated_at, deleted_at columns.

## Soft Deletes

One of the possible reasons for soft deletes are foreign keys:
once a parent record is referenced,
it can't be deleted by issuing a `DELETE` statement,
unless the `CASCADE` option has been specified on a child table.

So, create a deleted_at column which reflects whether a record is deleted or not.

## Money

To store money, use cents with `BIGINT` type.
Alternatively, `NUMERIC` type can be used.

## CHECK CONSTRAINT and NULL

The constraint of the form `CHECK amount >= 0` does not prevent amount from being set to `NULL`.
Use the `NOT NULL` constraint additionally on a column.

## EXCLUDE USING constraint

Ensure there is only one pending order per customer:

     ALTER TABLE sales.orders
     ADD CONSTRAINT one_pending_order_per_customer
     EXCLUDE USING btree (customer_id WITH =)
     WHERE (status = 'pending');

See "Just Use Postgres", 2.6.1 Functions: A practical example.

## TIMESTAMPTZ

TIMESTAMPTZ will always be stored in UTC time zone.

https://www.datacamp.com/doc/postgresql/timestamptz

## ALTER TABLE

`ALTER TABLE` allows you to change the table schema:

     ALTER TABLE products.reviews
     ALTER COLUMN review SET NOT NULL,
     ADD CONSTRAINT review_rank_check CHECK (rank BETWEEN 1 AND 5);

In the query above, two constraints are added.

Consider the usage of `VACUUM ANALYZE` after a table alteration.

## Generated columns

Generated columns are generated when `INSERT` or `UPDATE` happens.

     ALTER TABLE omdb.movies
     ADD COLUMN lexemes tsvector
     GENERATED ALWAYS AS (
      to_tsvector('english', coalesce(name, '') || ' ' || coalesce(description, ''))
     ) STORED;

A generated column can be stored, as in the example above, or a virtual.
A stored one is persisted on a disk,
whereas a virtual one is calculated on demand during `SELECT`.

Hence, a stored generated column is faster to retrieve, but it's slower to write.
For a virtual column, therefore, a reverse logic applies.

Since a virtual column is not persisted on a disk, it's impossible to index.

See "Just use Postgres", 6.2.2 Storing tsvector lexemes in the database.
