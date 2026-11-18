# Postgres Transactions and Locks

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

From Postgres documentation:

      A repeatable read transaction's snapshot
      is actually frozen at the start of its first query
      or data-modification command (SELECT, INSERT, UPDATE, DELETE, or MERGE),
      so it is possible to obtain locks explicitly before the snapshot is frozen.

https://www.postgresql.org/docs/current/applevel-consistency.html#NON-SERIALIZABLE-CONSISTENCY

### SERIALIZABLE

`SERIALIZABLE` guarantees that
a result of the committing a group of concurrent transactions
is consistent with at least one ordering of running these transactions one at a time, serially.

If a serialization anomaly is detected,
one transaction be allowed to commit, and the other will be rolled back.

Further, even in the case of read-only transactions at `SERIALIZABLE` level,
the data should only be considered valid only when a transaction commits successfully.

Note: `SERIALIZABLE` prevents write skews and is an alternative to `SELECT ... FOR UPDATE`.

Postgres doesn't allow you to use `SERIALIZABLE` for hot standbys or logical replicas:
https://www.postgresql.org/docs/current/applevel-consistency.html#SERIALIZABLE-CONSISTENCY

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

`SELECT ... FOR UPDATE` is an example of a row-level lock.

Understand: `SELECT ... FOR UPDATE` will not prevent a plain `SELECT` from reading the data.
Understand: the only way to prevent `SELECT` is to acquire `ACCESS EXCLUSIVE` lock.
Understand: depending on the isolation level, be ready to handle a possible serialization error.

https://www.postgresql.org/docs/current/applevel-consistency.html#NON-SERIALIZABLE-CONSISTENCY

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

## Transaction Retries

### Overview

Transactions with level `REPEATABLE READ`, `SERIALIZABLE`,
and also dead locks, have to be retried.

Once an error happens, its error code is returned, and therefore can be checked.

https://www.postgresql.org/docs/current/mvcc-serialization-failure-handling.html#MVCC-SERIALIZATION-FAILURE-HANDLING
