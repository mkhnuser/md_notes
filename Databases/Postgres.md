# Postgres

## Postmaster Process

### Overview

Postmaster process is responsible for creating other Postgres processes.

https://www.youtube.com/watch?v=S0LEDGbAnn8

### What happens during the client connection?

When a client connects to a Postgres instance,
a postmaster process will fork itself and create a dedicated process for a client;
Postgres calls this process Postgres backend.
After that, each query will be handled by this process.

## Shared memory

### Overview

Shared memory is shared among all Postgres processes, including Postgres client backends.
Shared memory is segmented. In particular, it contains:

* Shared buffers.
* WAL buffers.
* Memory for locks.

https://www.youtube.com/watch?v=S0LEDGbAnn8

### Shared buffers

When a client executes a query, the query executor will examine shared buffers for the data.
If the data is not present there, OS cache is examined.
If the data is not present there, the data is loaded from disk.
Similarly, when `INSERT` happens, the data is first stored in shared buffers.

### WAL buffers

WAL buffers contain changes which were made to the database data.

When an `UPDATE`, `INSERT`, or `DELETE` happens,
the change is first reflected in the WAL buffers.
After the data has been written to the WAL buffers,
WAL buffers will be flushed to the disk or to the OS cache.
After the flush has happened, the transaction is considered successful: a commit happens.

Understand: due to performance concerns, a commit is successful when:

1. `COMMIT` is encountered.
1. WAL buffers are successfully flushed.

not when shared buffers are flushed.

## Background processes

### Overview

Postgres has a set of background processes.

Some of them are responsible for flushing parts of shared memory.
For example, there are processes which flush shared buffers & WAL buffers.

## MVCC

### Overview

MVCC keeps track of the versions of a row.
Roughly speaking, when you begin a transaction,
you create a snapshot of the current database state.
Hence, transactions in Postgres will not be subjects of dirty reads.

https://www.youtube.com/watch?v=TBmDBw1IIoY
https://github.com/dmagda/DevMastersDb/blob/main/postgres/postgres_mvcc_backstage.md

### Tuple creation

When you perform `UPDATE` or `DELETE`, new tuple record will be created by MVCC.
The previous tuple record will contain a reference to the next tuple record.

## Vacuum

### Overview

Vacuum is a garbage collector which removes dead tuples which are created by MVCC.
Vacuum can create a performance hit if there are too many dead tuples.
Vacuum can be configured globally and on a per-table basis.

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

### VACUUM ANALYZE command

`VACUUM ANALYZE` will allow the query planner to use an index if it was just created,
as well as it will reclaim the space which was taken by the dead tuples.

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

## Logical Organization

### Overview

Postgres OS Process -> will contain a collection of databases -> each will contain schemas.

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
