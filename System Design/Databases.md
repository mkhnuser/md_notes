# Databases

## DB types and their usage

### Wide-column

Wide-column databases allow quick access on a per column basis.
This contrasts with a relational database, which operates on a per row basis.

So, wide-column databases load particular columns from a hard drive,
whereas relational ones load rows from a hard drive.

Use cases:

* Analytics;
* Sparse data.

Concrete examples:

* Clickhouse;
* Vertica.

### Key-value

Use cases:

* Sessions;
* Cart in an online shop.

### Document-oriented

The primary advantage of document-oriented databases is that they are schemaless.
The second advantage is that they allow data locality:
you store everything you need in one document.

Use cases:

* JSON Blobs;
* Catalogs, documents.

### Graph

Graph databases represent relations between two or more nodes.

### Fulltext search

Use one if you want to implement search on your blobs of data.

### Time-series

Use one if you have a strong connection between you data and a timestamp.

Concrete examples:

* Influxdb.

### Blob Storage

If you want to store audio, video, photos, you use a blob storage.

Concrete examples:

* Amazon S3.

### OLAP, OLTP, HTAP traffic

* OLAP = Online Analytical Processing.
* OLTP = Online Transactional Processing.
* HTAP = Hybrid Transactional / Analytical Processing.

Usually, there is a lot of OLTP requests, but few OLAP requests.
However, OLAP requests generate a lot of load, whereas OLTP don't.
Because of this, it makes sense to use separate databases based on these types of requests.

## Database Backups

Consider using database backups.

## Database Replication

The main difference between replication and backups is that replication
is an ongoing process, whereas backups are stored cold.

If a malicious actor decides to delete some data, replication is going to reflect these change across all replicas. However, backups will be intact.

Replication does not allow you to scale writing to a database,
only only allows you to scale reading from it.

### Replication Types

* Leader / follower:

      Write happens to a leader,
      Reading happens from both leaders and followers.

* Leader / Leader:

      Depending on a geolocation, for example,
      requests may be routed to a different leader.

      Be aware: write conflicts might happen.
      https://programmingappliedai.substack.com/p/how-do-we-resolve-write-conflicts

* Leaderless.

### How do you synchronize data between replicas?

* Sync replication (strong consistency - high latency);
* Async replication (eventual consistency - low latency).
* Semisync.

A database cluster might have both sync and async replicas.

### Failover

When a leader node dies, a failover process has to happen: a new leader has to be chosen.

### Hot standby replicas vs Warm standby replicas

Hot standby: followers accept read requests.
Warm standby: followers don't accept read requests, they are merely receiving the replicated data.

### Logical Replication vs Physical Replication

Physical replication copies the whole files,
whereas logical one copies records.

Logical replication is represented by:

* Statement Based Replication (SBR);
* Row Based Replication (RBR).
* Mixed.

## Data Partitioning

Partitioning allows you to partition a table into multiple ones.
This usually implies partitioning within the same schema (within one physical machine).

Vertical partitioning splits a table vertically;
you get two or more tables each containing a subset of columns of the original table.

Horizontal partitioning splits a table horizontally;
you get two or more tables each containing a subset of rows of the original table.

## Data Sharding

Sharding is the process of splitting data into datasets across multiple nodes.
For example, we can use sharding to partition a database as follows:
all users data is on machine number one;
all products data is on machine number two.

Each sharding zone has to be replicated separately.

## Consistent Hashing

Given many shards of data, we need to route the request to a particular shard
based on some field in this request. This is where classical (hashing + mod) might fail
if you want to add a new shard. To solve this problem, you introduce consistent hashing.

## Database Terminology

### ACID (Transactions)

An operation within a DB which satisfies ACID principles is called a transaction.

#### Atomicity

A transaction either fails or succeeds exclusively. The whole transaction is one unit.

#### Consistency

Consistency ensures that a DB transitions from one consistent state into another.
All constraints, cascades, triggers, etc. are applied.

#### Isolation

Isolation ensures that a state of a DB after concurrent transactions have been applied
is the same as it would have been if the transaction were executed sequentially.
There are many isolation levels.

#### Durability

Once a transaction commits, the data is permanently stored.

### Eventual Consistency (BASE)

If no new updates are made to data, eventually you will have access to the most recent state.

#### Basically Available

Basically Available state that read and writes are possible but you may not get the most recent state.

#### Soft-state

No consistency is guaranteed. We can only guess the current state of the system.

#### Eventually Consistent

If we wait long enough, we will get the most recent data.

### CAP Theorem

Partition-tolerant distributed data store may provide at most two of the following aspects:

1. Consistency: every client reading from any node receives the most recent information.
For a write operation to be successful, it has to be forwarded / replicated to all other nodes.

2. Availability: every request received by a non-failing node must produce a response.

When a network partition failure happens, you have to choose between the two options:

1. Abort the operation and therefore reduce availability in favor of consistency.
2. Proceed with the operation and provide availability possibly introducing inconsistency.

Important observation: in the absence of network partitioning, both aspects can be satisfied.
Modern technologies allow you to reduce network partitions to a minimum. That's why it is important to consider PACELC theorem.

### CAP theorem and databases

#### CA systems

Relational DBs are Consistent and Available, they are not Partition Tolerant by design.
This implies that these systems are often vertically scaled, but not horizontally.

#### CP systems

HBase, MongoDB, Redis.

#### AP systems

Cassandra, CouchDB, Dynamo.

### PACELC Theorem

PACELC Theorem expands CAP theorem.
If partition happens, you choose between consistency and availability. Else, you choose between latency and consistency.
