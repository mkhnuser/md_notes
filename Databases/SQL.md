# SQL

## General

A Role = User in the Database World.
*psql* terminal client uses the current user for the role and the database name to be connected to.
PK = NOT NULL + UNIQUE CONSTRAINT.
Recall that a PK can be natural and surrogate.

Think about always adding created_at, updated_at, deleted_at attributes.

COUNT(*) counts all strings, whereas COUNT(COLUMN) counts only NOT NULL strings.

Use IS NULL or IS NOT NULL for NULL comparison. != behaviour is tricky for NULL.
When you do ORDER BY remember about NULLS LAST, NULLS FIRST.

Normalization allows you to reduce data redundancy within a table; remove duplicates.
Normalization is achieved through a table schema restructuring.
Normalization is a gradual process; there are many normal forms.
If a table is in a normal form, it satisfies some set of constraints which is imposed on the table.

You usually use 1NF, 2NF, 3NF.

You can implement one-to-one relation using REFERENCES with UNIQUE constraint.
A foreign key must reference a primary key or a unique column.

## Transaction Isolation Levels

MVCC creates a snapshot of a DB before you execute a transaction.

Transaction isolation levels allow you to control how isolated a particular
transaction is compared to other concurrent transactions.

SQL Standard describes the following Transaction Isolation Levels:
* READ UNCOMMITTED: allows dirty reads.
* READ COMMITTED: solves dirty reads; allows phantom reads and non-repeatable reads.
* REPEATABLE READ: solves non-repeatable reads; allows phantom reads IN SOME DBs (not PostgreSQL); does not prevent serialization errors.
* SERIALIZABLE

SERIALIZABLE = The executing of multiple concurrent transaction equals the execution of these transactions in some order.

Transactions may fail on the DB level, so a developer must be ready to handle
Transaction Exceptions and to rerun these transactions - the whole idea
of atomicity is that you can rerun transactions safely.

In PostgreSQL, if you use SERIALIZABLE transaction level, you must use it for every transaction to avoid strange implicit behavior: if even one transaction
uses Transaction Isolation Level which is different from SERIALIZABLE,
then all transactions marked as SERIALIZABLE will be implicitly run
as REPEATABLE READ.

SERIALIZEBLE Isolation Level doesn't guarantee a specific order or execution.

PostgreSQL doesn't allow Dirty Reads to happen due to MVCC (recall snapshot creation prior to transaction begin).
PostgreSQL doesn't allow Phantom Read to happen in REPEATABLE READ transaction isolation level. Other DBs may allow it.

## Locking

There are situations where you want to have a finer-grade control over transactions (MVCC does not help). You use locks in these cases.

There is an explicit and an implicit locking.
Certain PostgreSQL commands acquire locks automatically.
You can explicitly lock the whole table or a specific row.
The stricter locking is, the less performant your app is.

Locking happens within a transaction.

A developer should be ready to handle deadlocks, which sometimes are automatically detected
and the whole transaction is rolled back.
It is possible to set timeouts for statements.

## Indexes

Indexes require disk space. Also, insertion speed decreases since indexes need to be updated every time an insertion happens.

## Misc

Perhaps transactions should be short-lived: one HTTP-request-response cycle so that transactions do not become idle.

`psql -h 127.0.0.1 -U app -d movies_database -f movies_database.ddl` - execute a file.
