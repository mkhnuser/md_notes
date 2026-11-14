# SQL in Postgres

## Overview

Here I note SQL standard that's used in Postgres.

## Primary Keys

### Overview

PK = NOT NULL + UNIQUE CONSTRAINT.
Recall that a PK can be natural and surrogate.
When a primary key is created, an index is created as well.

An example of ID:

    id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY

`GENERATED ALWAYS AS IDENTITY` prohibits a manual ID insertion.

### UUID as a primary key

UUID has the following advantages over a plain sequential id:

* UUID can be generated on a client:

      You don't have to rely on a database sequencing.

* UUID simplifies data sharding:

      You can insert records on multiple shards without relying on
      a central sequencing authority.

## NULL

### Overview

COUNT(*) counts all rows, whereas COUNT(COLUMN) counts only NOT NULL rows.
Use IS NULL or IS NOT NULL for NULL comparison. != behaviour is tricky for NULL.
When you do ORDER BY remember about NULLS LAST, NULLS FIRST.

## Normalization

### Overview

Normalization allows you to reduce data redundancy within a table.
You usually consider the usage of 1NF, 2NF, 3NF.

## Foreign References

### What can a foreign key reference?

A foreign key must reference a primary key or a unique column.

### NOT NULL has to be explicit

Foreign key does not prohibit a NULL to be present.
If you want to enforce a reference to an external column, use `NOT NULL` constraint.

### One-to-one references

You can implement one-to-one relation using REFERENCES with UNIQUE constraint.

## Schema Design

### Markers

Always add created_at, updated_at, deleted_at columns.

### Soft Deletes

One of the possible reasons for soft deletes are foreign keys:
if a record is referenced, it can't be deleted by issuing a `DELETE` statement.
So, create `deleted_at` column which reflects whether a record is deleted or not.

### Money

To store money, use cents with `BIGINT` type.
Alternatively, `NUMERIC` type can be used.

### CHECK CONSTRAINT and NULL

`CHECK amount >= 0` does not prevent `amount` from being set to `NULL`.
Use `NOT NULL` additionally.

### EXCLUDE USING constraint

     ALTER TABLE sales.orders
     ADD CONSTRAINT one_pending_order_per_customer
     EXCLUDE USING btree (customer_id WITH =)
     WHERE (status = 'pending');

See "Just Use Postgres", 2.6.1 Functions: A practical example.

### TIMESTAMPTZ

TIMESTAMPTZ will always be stored in UTC time zone.

https://www.datacamp.com/doc/postgresql/timestamptz

## ALTER TABLE

### Overview

`ALTER TABLE` allows you to change the table schema:

     ALTER TABLE products.reviews
     ALTER COLUMN review SET NOT NULL,
     ADD CONSTRAINT review_rank_check CHECK (rank BETWEEN 1 AND 5);

In the query above, two constraints are added.

Consider the usage of `VACUUM ANALYZE` after a table alteration.

## Views

### Overview

Views allow you to execute a complex query using a name for this query.
Views are stored within a particular schema can be reused among many clients.
Since views are reused, your applications might not need to store complex SQL statements.

### Types of views

There are plain views and materialized views:
plain views are always executed, whereas materialized ones executed only once.
Materialized views are materialized during creation and can be refreshed when needed.
