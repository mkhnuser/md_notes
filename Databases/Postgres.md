# Postgres

## MVCC

MVCC creates a snapshot of a database before you execute a transaction.
Hence, transactions are isolated, but the level of isolation can be controlled.

## Postgres Transactions

Transaction isolation levels:

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

SERIALIZABLE checks whether the executing of multiple concurrent transaction equals the execution of these transactions in some order.
SERIALIZABLE isolation level doesn't guarantee a specific order of execution of transactions; it guarantees that there is order.

! Transactions fail, so you should be ready to rerun them in your code.
The whole idea of atomicity is to be able to rerun transactions.
So, be prepared to rerun REPEATABLE READ and SERIALIZABLE transactions.

Postgres doesn't allow dirty reads to happen due to MVCC.
Postgres doesn't allow phantom reads to happen in a REPEATABLE READ transaction isolation level. Other databases, however, may allow it.

Ideally, transactions should be short-lived:
only one HTTP-request-response cycle so that transactions do not become idle.

## Locks

There are situations where you want to have a finer-grade control over transactions (MVCC does not help). You use locks in these cases.

One acquires locks only within a transaction;
there is an explicit and an implicit locking.

* Implicit locking refers to the fact that certain PostgreSQL commands acquire locks automatically.
* One can explicitly lock the whole table or a specific row. The stricter locking is, the less performant your app is.

One should be ready to handle deadlocks, which sometimes are automatically detected
and the whole transaction is rolled back;
it is possible to set timeouts for statements which involve locks.

## psql

`psql -h 127.0.0.1 -U app -d movies_database -f movies_database.ddl` - execute a file.
*psql* terminal client uses the current user for the role and the database name to be connected to.

## Misc

An outline of postgres: https://proselyte.net/postgres-for-devs/.
