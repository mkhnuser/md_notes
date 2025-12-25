# Postgres

## Primary Keys

PK = NOT NULL + UNIQUE CONSTRAINT.
Recall that a PK can be natural and surrogate.
You might want to consider the usage of UUIDs for ease of sharding.

## NULL

COUNT(*) counts all strings, whereas COUNT(COLUMN) counts only NOT NULL strings.
Use IS NULL or IS NOT NULL for NULL comparison. != behaviour is tricky for NULL.
When you do ORDER BY remember about NULLS LAST, NULLS FIRST.

## Normalization

Normalization allows you to reduce data redundancy within a table; remove duplicates.
Normalization is achieved through a table schema restructuring.
Normalization is a gradual process; there are many normal forms.
If a table is in a normal form, it satisfies some set of constraints which is imposed on the table.

You usually use 1NF, 2NF, 3NF.

## Foreign References

You can implement one-to-one relation using REFERENCES with UNIQUE constraint.
A foreign key must reference a primary key or a unique column.

## Transactions

MVCC creates a snapshot of a DB before you execute a transaction.
Transaction isolation levels allow you to control how isolated a particular
transaction is compared to other concurrent transactions.

SQL Standard describes the following Transaction Isolation Levels:

* READ UNCOMMITTED: allows dirty reads.
* READ COMMITTED: solves dirty reads; allows phantom reads and non-repeatable reads.
* REPEATABLE READ: solves non-repeatable reads; allows phantom reads IN SOME DBs (not PostgreSQL); does not prevent serialization errors.
* SERIALIZABLE.

SERIALIZABLE = the executing of multiple concurrent transaction equals the execution of these transactions in some order.
SERIALIZEBLE isolation level doesn't guarantee a specific order of execution;
it guarantees that there is order.

Transactions fail, so you should be ready to rerun them in your code.
The whole idea of atomicity is to rerun transactions.

Postgres doesn't allow Dirty Reads to happen due to MVCC.
Postgres doesn't allow Phantom Reads to happen in REPEATABLE READ transaction isolation level. Other databases, however, may allow it.

## Locks

There are situations where you want to have a finer-grade control over transactions (MVCC does not help). You use locks in these cases.

One acquires locks only within a transaction;
there is an explicit and an implicit locking.

* Implicit locking refers to the fact that certain PostgreSQL commands acquire locks automatically.
* One can explicitly lock the whole table or a specific row. The stricter locking is, the less performant your app is.

One should be ready to handle deadlocks, which sometimes are automatically detected
and the whole transaction is rolled back;
it is possible to set timeouts for statements which involve locks.

## Indexes

Consider these disadvantages of using indexes:

* Indexes require disk space;
* Insertion and update speed decreases since indexes need to be updated.

In general,
if number of writes is drastically more than number of reads,
you shouldn't use indexes.

## Misc

Perhaps transactions should be short-lived: one HTTP-request-response cycle so that transactions do not become idle.

`psql -h 127.0.0.1 -U app -d movies_database -f movies_database.ddl` - execute a file.

*psql* terminal client uses the current user for the role and the database name to be connected to.

Always add created_at, updated_at, deleted_at attributes.
