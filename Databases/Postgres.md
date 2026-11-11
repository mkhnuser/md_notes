# Postgres

## Logical Organization

### Overview

Postgres OS Process -> a collection of databases -> schemas.

## MVCC

### Overview

MVCC keeps track of the versions of a row.
Roughly speaking, when you begin a transaction,
you create a snapshot of the current database state.
Hence, transactions in Postgres will not be subjects of dirty reads.

https://www.youtube.com/watch?v=TBmDBw1IIoY
https://github.com/dmagda/DevMastersDb/blob/main/postgres/postgres_mvcc_backstage.md

## Vacuum

### Overview

Vacuum is a garbage collector which removes dead tuples which are created by MVCC.
Vacuum can create a performance hit if there are too many dead tuples.
Vacuum can be adjusted globally and on a per-table basis.

https://www.youtube.com/watch?v=TBmDBw1IIoY
https://github.com/dmagda/DevMastersDb/blob/main/postgres/postgres_mvcc_backstage.md

### VACUUM command

To invoke vacuum on a table, use: `VACUUM table_name;`.
Having issued the command, the dead tuples of `table_name` will be deleted.
Moreover, the space which was occupied by the dead tuples will be reused for future MVCC records.

### VACUUM FULL command

To invoke full vacuum on a table, use: `VACUUM FULL table_name;`.
After the full vacuum, the dead tuples are deleted,
and the space which was occupied by the dead tuples is release to the OS.

### Auto vacuum

Postgres performs vacuum automatically when a certain dead tuples threshold is passed.
However, the defaults are conservative and might not be appropriate for write-heavy applications.

### Possible auto vacuum problems

* Auto vacuum runs, but is so slow that it never gets done.
* Auto vacuum runs, but a long running open transaction prevents it from removing dead tuples.
* Other tables need to be vacuumed more urgently to avoid transaction ID wraparound.

      So the autovacuum workers are busy with other things.

* Auto vacuum runs, but conflicts with concurrent locks on a table.

      LOCK TABLE, ALTER TABLE, etc.
      This makes autovacuum give up and try again later.

* Auto vacuum is disabled, either globally or for a table.

https://stackoverflow.com/questions/67468949/understanding-auto-vacuum-and-when-it-is-triggered
https://www.cybertec-postgresql.com/en/author/laurenz_albe/
https://github.com/laurenz

## Transactions in Postgres

### Transaction isolation levels

* READ UNCOMMITTED:

      In Postgres, in mode is equivalent to READ COMMITTED due to MVCC.
      In other databases, dirty reads are possible.

* READ COMMITTED:

      Solves dirty reads problem;
      allows phantom reads and non-repeatable reads.

* REPEATABLE READ:

      Solves non-repeatable reads;
      solves phantom reads (in PostgreSQL, other databases might not solve it);
      does not prevent serialization errors.

* SERIALIZABLE.

Postgres doesn't allow dirty reads to happen due to MVCC.
Postgres doesn't allow phantom reads to happen in a REPEATABLE READ transaction isolation level. Other databases, however, may allow it.

### SERIALIZABLE

SERIALIZABLE checks whether the executing of multiple concurrent transaction equals the execution of these transactions in some order.
SERIALIZABLE isolation level doesn't guarantee a specific order of execution of transactions; it guarantees that there is order.

### Atomicity

! Transactions fail, so you should be ready to rerun them in your code.
The whole idea of atomicity is to be able to rerun transactions.
So, be prepared to rerun REPEATABLE READ and SERIALIZABLE transactions.

## Schemas

### Overview

Schemas create a namespace for tables, indexes, views, functions, etc.

### Joins between schemas

Joins between schemas are possible.

## psql

### Execute a file

        psql -h 127.0.0.1 -U app -d movies_database -f movies_database.ddl

### Default role and default database

Psql uses the current user for the role and the database name to be connected to.
