# Postgres Schemas and Indexes

## Schemas

### Overview

Schemas create a namespace for tables, indexes, views, functions, etc.

### Default Schemas

`SHOW search_path;` will display the schemas which will be used, in order.

### Joins on schemas

Joins between different schemas are possible.
Joins between different databases are not automatically possible.

## Indexes

### Automatically created indexes

Indexes are created automatically for `PRIMARY KEY` and `UNIQUE` columns.

### Single-column indexes

...

### Composite indexes

Composite indexes are created on multiple columns: (`c1`, `c2`, `c3`, ...).
Postgres will form the index sequentially: first for `c1`, then, within `c1` group, for `c2`, etc.
Postgres will utilize the composite index if `c1` is present in a `WHERE` clause.

The order of columns in a `WHERE` clause matters,
see "Just use Postgres", 4.6.3 Caveats of composite indexes on this matter.

### Covering indexes

Covering indexes store table columns inside the index so that table rows don't have to be accessed.

An example of a covering index:

      CREATE INDEX idx_composite_covering_index
      ON game.player_stats (region, score DESC, win_count DESC)
      INCLUDE (username);

See "Just use Postgres", 4.7 Covering indexes.

### Partial Indexes (Filtered Indexes)

A partial index is only created for a subset of data.
That is, an index works only for a subset of rows:

      CREATE INDEX partial_index_name ON table_name(columnA) WHERE condition;

See "Just use Postgres", 4.8 Partial indexes.

### Functional Indexes (Expression Indexes)

Functional indexes index an application of some SQL function to a set of columns:

      CREATE INDEX functional_index_name
      ON table_name(function_or_expression(columnA, [additional_columns]))

See "Just use Postgres", 4.9 Functional and expression indexes.
See "Just use Postgres", 5.6.1 Using an expression index with a B-tree.

### B-tree index

B-tree is of great use for comparison operators and `BETWEEN`.
Overall, B-tree works well for ranges, numbers, and strings.

See "Just use Postgres", 4.5.1 Single-column B-tree indexes.
See "Just use Postgres", 5.6.1 Using an expression index with a B-tree.

### Hash index

Hash index works similar to a hash table and is used only for an `=` and `IN`.

See "Just use Postgres", 4.5.2 Single-column hash indexes.

### GIN index

Generalized Inverted Index is a great choice for indexing JSON structures.
See "Just use Postgres", 5.6.2 Using GIN indexes.

## ANALYZE

Consider the usage of `ANALYZE` after the index creation:

      CREATE INDEX on tableA(columnB);
      ANALYZE tableA;

So that a query planner is updated.

See "Just use Postgres", 4.5.1 Single-column B-tree indexes.

## EXPLAIN

`EXPLAIN` is used to see how a query will be executed by a query planner.
The query itself is not run.

See "Just use Postgres", 4.4 Learning to use the EXPLAIN statement.

## EXPLAIN ANALYZE

`EXPLAIN ANALYZE` shows how a query will be executed and also executes a query.
Since a query is run, additional execution metrics will be provided as well.

Make sure to execute `EXPLAIN ANALYZE` multiple times if possible,
since Postgres refines the query execution strategy as the query executes.

See "Just use Postgres", 4.4 Learning to use the EXPLAIN statement.
