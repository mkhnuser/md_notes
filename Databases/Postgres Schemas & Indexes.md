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

Indexes are created automatically for primary keys and unique columns.
