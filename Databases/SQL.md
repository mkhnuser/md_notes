# SQL

## Primary Keys

PK = NOT NULL + UNIQUE CONSTRAINT.

Recall that a PK can be natural and surrogate.
You might want to consider the usage of UUID for a primary key.
It has the following advantages over a plain id:

* UUID can be generated on a client:

      You don't have to rely on a database sequencing.

* UUID simplifies data sharding:

      You can insert records on multiple shards without relying on
      a central sequencing authority.

## NULL

COUNT(*) counts all rows, whereas COUNT(COLUMN) counts only NOT NULL rows.
Use IS NULL or IS NOT NULL for NULL comparison. != behaviour is tricky for NULL.
When you do ORDER BY remember about NULLS LAST, NULLS FIRST.

## Normalization

Normalization allows you to reduce data redundancy within a table.
You usually consider the usage of 1NF, 2NF, 3NF.

## Foreign References

### One-to-one references

You can implement one-to-one relation using REFERENCES with UNIQUE constraint.

### What can a foreign key reference?

A foreign key must reference a primary key or a unique column.

## Misc

Always add created_at, updated_at, deleted_at columns.
