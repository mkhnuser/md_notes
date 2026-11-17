# Postgres

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

## Transactions in Postgres

### Implicit transactions

When you issue `INSERT`, `DELETE`, `CREATE TABLE`, `ALTER TABLE`,
Postgres wraps these statements with `BEGIN` and `COMMIT` statements.

That way, consistency is achieved:
if anything happens, partial updates to the database are rolled back.

### Transaction isolation levels

* READ UNCOMMITTED:

      In Postgres, in mode is equivalent to READ COMMITTED due to MVCC.
      In other databases, dirty reads are possible.

* READ COMMITTED:

      Solves dirty reads problem;
      However, non-repeatable reads and phantom reads are possible.

* REPEATABLE READ:

      Solves non-repeatable reads and phantom reads.
      However, serialization exceptions are possible.

      Note: phantom reads are solved in Postgres, other databases may allow them at this level.

* SERIALIZABLE.

### READ COMMITTED

When `UPDATE` or `DELETE` happens on a row within a transaction which is run at this level,
the transaction will attempt to acquire a lock on the row,
by first waiting till another transaction releases a lock on the row,
if any lock was acquired by a concurrent transaction on the row in the first place.

Suppose a row lock has finally been acquired after waiting for another transaction:

      If the concurrent transaction has rolled back, the original row is just used.
      If the concurrent transaction has committed and deleted the row, no operation is done.

      If the concurrent transaction has committed and updated the original row,
      then the updated row is used and `WHERE` condition is reevaluated on the updated row,
      and if the `WHERE` condition reevaluation doesn't match the updated row,
      no operation is done.

See "Just Use Postgres", 2.4.3 Multiversion concurrence control.

### REPEATABLE READ

Suppose you perform `UPDATE` or `DELETE` on a row, and hence you attempt to acquire a row lock.
Suppose further that a concurrent transaction has already acquired the lock.
Because of this, you wait till the concurrent transaction commits or aborts.
If the concurrent transaction commits,
and the row is updated or deleted,
a serialization error is raised.

Once a serialization error has been raised, Postgres aborts the transaction.
Consequently, you must roll it back, and then potentially rerun a transaction.

Understand: a read-only transaction will never have a serialization error.

Understand: at this level, write skews are not prevented.
To prevent write skews, explicit locks have to be used at this isolation level.

### SERIALIZABLE

`SERIALIZABLE` guarantees that
a result of the committing a group of concurrent transactions
is consistent with at least one ordering of running these transactions one at a time, serially.

If a serialization anomaly is detected,
one transaction be allowed to commit, and the other will be rolled back.

Further, even in the case of read-only transactions at `SERIALIZABLE` level,
the data should only be considered valid only when a transaction commits successfully.

Note: `SERIALIZABLE` prevents write skews and is an alternative to `SELECT ... FOR UPDATE`.

### Atomicity

The whole idea of atomicity is to be able to rerun transactions safely.
Be prepared to rerun `REPEATABLE READ` and `SERIALIZABLE` transactions due to possible errors.

### Atomicity and Sequences

Sequences are not rolled back if a transaction roll back happens.
https://www.postgresql.org/docs/current/transaction-iso.html

### Transaction rollbacks and MVCC

Even if a rollback happens, MVCC has already captured the partial changes, so vacuum is needed.
See "Just Use Postgres", Extract 2.4.2 Explicit transactions.

## Locks

### Locks Names

Understand:
due to historical reasons,
lock names can contain a word "row", but a lock, in fact, is applied to a table.

### Locks life cycle

Locks are acquired within a transaction and are released when a transaction is finished.
However, savepoints are respected: if a lock is acquired after a savepoint
and you roll back to a savepoint, lock is released.

### Locks types

There are:

* Table-level locks;
* Row-level locks;
* Page-level locks.

### Mutual Exclusion

Concurrent transactions can't hold locks of conflicting modes on a resource.
Therefore, multiple transactions can hold locks of non-conflicting modes on a resource.

### No exclusion within one transaction

However, locks never conflict within the very same transaction:
for example, you can hold both `ACCESS EXCLUSIVE` and `ACCESS SHARE` locks simultaneously.

### SELECT ... FOR UPDATE

Understand: `SELECT ... FOR UPDATE` will not prevent a plain `SELECT` from reading the data.
Understand: depending on the isolation level, be ready to handle a possible error.

### Locks can trigger disk access

https://www.postgresql.org/docs/current/explicit-locking.html#LOCKING-ROWS

### Deadlocks Overview

Suppose transaction A hold a lock on table 1 and tries to acquire a lock on table 2.
Suppose further transaction B holds a lock on table 2 and tries to acquire a lock on table 1.
Then Postgres realizes that there is a deadlock and aborts one of the transactions.
Other concurrent transactions will be allowed to continue.
One can't predict which transaction is aborted.

https://www.postgresql.org/docs/current/explicit-locking.html#LOCKING-DEADLOCKS

### Deadlocks can occur even when no explicit locking is used

Understand: deadlocks are possible even if no explicit locks are used,
so be ready to rerun transactions.

https://www.postgresql.org/docs/current/explicit-locking.html#LOCKING-DEADLOCKS

### Why long running transactions are bad?

Long running transactions might prevent other transactions from acquiring locks on resources.

https://www.postgresql.org/docs/current/explicit-locking.html#LOCKING-DEADLOCKS

### Locks Statistics

Locks statistics are stored at `pg_locks` table.

### Advisory Locks

https://www.postgresql.org/docs/current/explicit-locking.html#LOCKING-DEADLOCKS

## Logical Organization

### Overview

Postgres OS Process -> will contain a collection of databases -> each will contain schemas.

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

## Roles and Access

### Roles

Each connection has an associated role with it.

### postgres role

postgres role is all-permissive and should be avoided for production purposes.

### Role creation

        CREATE ROLE coffee_chain_admin WITH LOGIN PASSWORD 'password';
        GRANT CONNECT ON DATABASE coffee_chain TO coffee_chain_admin;
        REVOKE CONNECT ON DATABASE coffee_chain FROM PUBLIC;

See roles discussion in "Just Use Postgres", 2.8 Roles and access control.

## psql

### Default role and default database

Psql uses the current user for the role and the database name to be connected to.

### Execute a file

        psql -h 127.0.0.1 -U app -d movies_database -f movies_database.ddl
        docker exec -it postgres psql -U postgres -c "\i /home/streaming_data.sql"

### List schemas

Use `\dn` to list schemas.

### List roles

Use `\du` to list roles.
