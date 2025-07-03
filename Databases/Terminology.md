# Terminology


## Availability and Scalability


### Partitioning

Partitioning allows you to partition a table into multiple ones.
This usually implies partitioning within the same schema (within one physical machine).

Vertical partitioning splits a table vertically;
you get two or more tables each containing a subset of columns of the original table.

Horizontal partitioning splits a table horizontally;
you get two or more tables each containing a subset of rows of the original table.

### Sharding

Sharding is the process of splitting data into datasets across multiple nodes.
For example, we can use sharding to partition a database as follows:
all users data is on machine number one;
all products data is on machine number two.

### Replication

Replication is a physical copy of all data across multiple databases.
Each replica is kept in sync with the master node.
Replicas contain all the data of the master node.


## ACID (Transactions)


An operation within a DB which satisfies ACID principles is called a transaction.

### Atomicity

A transaction either fails or succeeds exclusively. The whole transaction is one unit.

### Consistency

Consistency ensures that a DB transitions from one consistent state into another.
All constraints, cascades, triggers, etc. are applied.

### Isolation

Isolation ensures that a state of a DB after concurrent transactions have been applied
is the same as it would have been if the transaction were executed sequentially.
There are many isolation levels.

### Durability

Once a transaction commits, the data is permanently stored.


## Eventual Consistency (BASE)

If no new updates are made to data, eventually you will have access to the most recent state.

### Basically Available

Basically Available state that read and writes are possible but you may not get the most recent state.

### Soft-state

No consistency is guaranteed. We can only guess the current state of the system.

### Eventually Consistent

If we wait long enough, we will get the most recent data.


## CAP Theorem

Distributed data store may provide *at most* two of the following three aspects:

1. Consistency: every read receives the most recent write (do not confuse with consistency in ACID).
2. Availability: every request received by a non-failing node must produce a response.
3. Partition Tolerance:

    The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes.

When a network partition failure happens, you have to choose between the two options:

1. Abort the operation and therefore reduce availability in favor of consistency.
2. Proceed with the operation and provide availability possibly introducing inconsistency.

In the absence of Network Partitioning, both aspects can be satisfied.


## PACELC Theorem


TODO.
