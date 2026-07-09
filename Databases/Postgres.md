# Postgres

## MVCC

MVCC creates a snapshot of a database before you execute a transaction.
Hence, transactions are isolated, but the level of isolation can be controlled.

## Transactions in Postgres

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

## psql

`psql -h 127.0.0.1 -U app -d movies_database -f movies_database.ddl` - execute a file.
*psql* terminal client uses the current user for the role and the database name to be connected to.
