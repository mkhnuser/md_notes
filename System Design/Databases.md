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
You should have two or three backup files, ideally.
Understand: it takes some time to spin up a new database instance with backups applied.

## Database Replication

The main difference between replication and backups is that replication
is an ongoing process, whereas backups are stored cold.

If a malicious actor decides to delete some data, replication is going to reflect these change across all replicas. However, backups will be intact.

Replication does not allow you to scale writing to a database,
it only only allows you to scale reading from it.

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

Physical replication copies the whole files, whereas logical one copies records.

Logical replication is represented by:

* Statement Based Replication (SBR);
* Row Based Replication (RBR).
* Mixed.

## Data Partitioning

Partitioning allows you to partition (to split) a table into multiple ones.
Partitioning happens on precisely on machine.

Vertical partitioning splits a table vertically: you get two or more tables,
each containing a subset of columns of the original table.

Horizontal partitioning splits a table horizontally: you get two or more tables,
each containing a subset of rows of the original table.

### How do you choose a partition key?

The process of choosing a partition key is identical
to the process of choosing a sharding key.

## Data Sharding

Sharding is the process of splitting data into datasets across multiple nodes.
Thus, a centralized point of failure is eliminated.

For example, we can use sharding to partition a database as follows:

* All users data is on machine number one;
* All products data is on machine number two.

So, each shard has its own portion of data,
whereas each replica contains its own copy of data.
Even further, each shard can contains its own replicas.

Therefore, sharding is used to increase write throughput of your application.

### How do you choose a sharding key?

* Range-based sharding;
* Hash-based sharding;
* Directory-based sharding;
* Geographical sharding.

### Resharding

* Vbuckets (virtual shards);
* Consistent hashing.
* Rendezvous hashing.

## Consistent Hashing

Understand: consistent hashing is applied not only to resharding.
For example, it can be used if new buckets are to be added to the hash table:

        https://neetcode.io/problems/design-hashset/solution

## CAP Theorem

Partition tolerant distributed data store can provide at most two of the following:

1. Consistency:

        Every client reading from any node receives the most recent information.
        For a write operation to be successful,
        it has to be forwarded / replicated to all other nodes first.

2. Availability:

        Every request received by a non-failing node must produce a response.

When a network partition failure happens, you have to choose between the two options:

1. Abort the operation and therefore reduce availability in favor of consistency.
2. Proceed with the operation and provide availability possibly introducing inconsistency.

Understand: in the absence of network partitioning, both aspects can be satisfied;
consider an application which runs on precisely one host.

Modern technologies allow you to reduce network partitions to a minimum.
That's why it is important to consider PACELC theorem.

## PACELC theorem

PACELC theorem expands the CAP theorem:
if partition happens, you choose between consistency and availability.
Else, you choose between latency and consistency.

## BASE acronym

BASE = basically available, soft state, and eventually consistent.
BASE is the opposite to ACID.

## Misc

A wonderful article which goes in depth on sharding: https://proselyte.net/sharding-postgresql/
