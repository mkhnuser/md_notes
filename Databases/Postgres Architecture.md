# Postgres Architecture

## Postmaster Process

### Overview

Postmaster process is responsible for creating other Postgres processes.

https://www.youtube.com/watch?v=S0LEDGbAnn8
https://www.youtube.com/watch?v=Vq34xPYZwXg

### Connections to Postgres

When a client connects to a Postgres instance,
a postmaster process will fork itself and create a dedicated OS process for a client.

Postgres calls a client process a backend.
After that, each query will be handled by a backend.

When a client disconnects,
the postgres backend process which was responsible for the connection is terminated.

## Shared memory

### Overview

Shared memory is shared among all Postgres processes, including Postgres client backends.
Shared memory is segmented. In particular, it contains:

* Shared buffers.
* WAL buffers.
* Memory for locks.

https://www.youtube.com/watch?v=S0LEDGbAnn8

### Shared buffers

Shared buffers hold data pages and indexes and allow for a fast data look up.

When a client executes a query,
the query executor will examine shared buffers for the data page.
If the data is not present there, OS cache is examined.
If the data is not present there, the data is loaded from disk.

Similarly, when `UPDATE` happens, the data is first stored in shared buffers.

### WAL buffers

WAL buffers contain changes which were made to the database data.

When an `UPDATE`, `INSERT`, or `DELETE` happens,
the change is first reflected in the WAL buffers.
After the data has been written to the WAL buffers,
WAL buffers will be flushed to the disk or to the OS cache.
After the flush has happened, the transaction is considered successful: a commit happens.

Understand: due to performance concerns, a commit is successful when:

1. `COMMIT` statement is encountered.
1. WAL buffers are successfully flushed.

not when shared buffers are flushed.

### Shared buffers and WAL buffers link

Since WAL is responsible for whether a transaction is successful or not,
WAL buffers are flushed to the disk first, and only after that shared buffers are flushed.

## Auxiliary Processes

### Overview

Postgres has a set of background processes:

* Logger.
* Checkpointer.
* Auto vacuum workers.
* WAL writer.
* etc.

## MVCC

### The purpose of MVCC

MVCC allows write queries to not be blocked by read queries, and vice versa.
Additionaly, MVCC and row-level locking prevent dirty writes.
See "Just Use Postgres", 2.4.3 Multiversion concurrence control.

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
You might want to use it after the `ALTER TABLE` statement.

### Auto vacuum

Postgres performs vacuum automatically when a certain dead tuples threshold is passed.
The threshold is calculated by a formula.
Auto vacuum defaults are conservative and might not be appropriate for write-heavy applications.

### Possible auto vacuum problems

* Auto vacuum runs, but is so slow that it never gets done.
* Auto vacuum runs, but a long running open transaction prevents the removal of dead tuples.
* Other tables need to be vacuumed more urgently to avoid transaction ID wraparound.

      So the autovacuum workers are busy with other things.

* Auto vacuum runs, but conflicts with concurrent locks on a table.

      LOCK TABLE, ALTER TABLE, etc.
      This makes autovacuum give up and try again later.

* Auto vacuum might be disabled, either globally or for a table.

https://stackoverflow.com/questions/67468949/understanding-auto-vacuum-and-when-it-is-triggered
https://www.cybertec-postgresql.com/en/author/laurenz_albe/
https://github.com/laurenz

## Logical Database Organization

### Overview

Postgres OS Process -> will contain a collection of databases -> each will contain schemas.
