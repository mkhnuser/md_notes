# Databases

## DB types and their usage

### Relational

Relational databases load the whole rows from a hard drive.

Use cases:

* OLTP traffic.

### Column-based

Column-based databases load particular columns from a hard drive.

Use cases:

* OLAP traffic;
* Sparse data.

Concrete examples:

* Clickhouse;
* Vertica.

### Key-value

Use cases:

* Sessions;
* Cart in an online shop;
* Cache.

### Document-oriented

The primary advantage of document-oriented databases is that they are schemaless.
Another advantage is data locality:
you store everything you need in just one document,
which is critical for read-heavy applications because no joins are needed.

Use cases:

* JSON Blobs;
* Catalogs, documents, resumes.

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

## OLAP, OLTP, HTAP traffic

* OLAP = Online Analytical Processing.
* OLTP = Online Transactional Processing.
* HTAP = Hybrid Transactional / Analytical Processing.

Usually, there is a lot of OLTP requests, but few OLAP requests.
However, OLAP requests generate a lot of load, whereas OLTP don't.
Because of this, it makes sense to use separate databases based on these types of requests.

## Tools and Databases

Ensure that version of tools are compatible with version of databases.
For example, `pg_dump` version 9.2 won't work with Postgres 9.6.

## Database Backups

Consider the usage of many backup files during various time spans.

## Database Replication

### Overview

Understand: replication does not scale writes, it scales reads.

The difference between replication and backups
is that replication is an ongoing process, whereas backups are stored cold.

If a malicious actor decides to delete data,
replication will replicate these changes across all replicas.
However, backups will be intact if a malicious action has been performed.

That's the reason why ideally you should have both replication and backups.

### Replication Types

* Leader / follower:

      Write happens to a leader,
      Reading happens from both leaders and followers.

* Leader / Leader:

      A leader is chosen based on user's location, for example.
      Leaders are usually distributed across multiple regions.

      When a leader receives a write, it replicates it to all other leaders.
      Ensure you handle write conflicts: manually or automatically.

* Leaderless.

### How do you synchronize data between replicas?

* Synchronous replication: consistency over low latency.

      If at least one follower fails, all writes within a leader are blocked.

* Asynchronous replication: low latency over consistency.

      If data has not been replicated and a leader fails, the data is lost.

* Semisync: some replicas are synchronous, and some are not.

### Hot standby replicas vs Warm standby replicas

Hot standby: followers accept read requests.
Warm standby: followers don't accept read requests, they are merely receiving the replicated data.

### Logical Replication vs Physical Replication

Physical replication copies underlying data files.
In case of Postgres, WAL records are replicated.

Logical replication is represented by:

* Statement Based Replication (SBR);

      The whole SQL statements are replicated.

* Row Based Replication (RBR).

      Given a row, a log of changes to the row are replicated.

### Failover

When a leader, a failover process has to happen:

* A new leader has to be chosen.
* Clients have to perform writes to the new leader.
* Followers have to start accept replication stream from the new leader.

Be sure to examine your caching strategy in case of failover: should cache be invalidated?

### Problems with Replication Lag

If asynchronous replication is used, replication lag can introduce anomalies:

1. An inconsistent view of a read after a write.

        A user's request is processed by a replica
        which is not yet synced with a leader node.

2. A move backward in time.
3. An observer confusion.

## Data Partitioning

### Overview

Partitioning allows you to partition (to split) a table into multiple ones.
Partitioning happens on precisely one machine.

Vertical partitioning splits a table vertically:
you get two or more tables,
each containing a subset of columns of the original table.

Horizontal partitioning splits a table horizontally:
you get two or more tables,
each containing a subset of rows of the original table.

### How do you choose a partition key?

The process of choosing a partition key is identical
to the process of choosing a sharding key.

## Data Sharding

### Overview

Data sharding = split data writes into datasets across multiple nodes using a sharding key.

For example, we can use sharding to partition a database as follows:

* All users data is on machine number one;
* All products data is on machine number two.

Each database shard can be replicated.
In a leader / follower case, each shard will be a leader.

### How do you choose a sharding key?

* Range-based sharding;
* Hash-based sharding;
* Directory-based sharding;
* Geographical sharding.

### Data Locality

When you choose a sharding key, consider the locality of your data.

      For example, in a social media application, one might choose a user id as a sharding key.
      Then all data entities which contains the same user id will be present within one shard.

      JOINs and analytics can be performed easily:
      all data is local to only one shard, no other shards have to be queried.

### Resharding

* Vbuckets (virtual shards);

      Consider connecting to a set of virtual buckets, not an actual shards.

* Consistent hashing.
* Rendezvous hashing.

## Consistent Hashing

Understand: consistent hashing is applied not only to resharding.
For example, it can be used if new buckets are to be added to the hash table:

        https://neetcode.io/problems/design-hashset/solution

## CAP Theorem

In case of a network partition,
partition-tolerant distributed data store can provide precisely one guarantee:

1. Consistency:

        Every client reading from any node receives the most recent information.
        For a write operation to be successful,
        it has to be forwarded / replicated to all other nodes first.

2. Availability:

        Every request received by a non-failing node must produce a response.

When a network partition happens, you have to choose between the two options:

1. Abort the operation: consistency over availability.
2. Proceed with the operation: availability over consistency.

If a network partition is not present, both consistency and availability can be achieved;
consider an application which runs on precisely one host.

Nowadays network partition are reduced to a minimum;
that's why it is important to consider PACELC theorem.

## PACELC theorem

PACELC theorem expands the CAP theorem:

      If partition happens, choose between consistency and availability.
      Else, you choose between latency and consistency.

## BASE acronym

BASE = basically available, soft state, and eventually consistent.
BASE is the opposite to ACID.

## Two Phase Commit (2PC)

You can use 2PC if you want to perform a distributed transaction.

## SAGA

You can use SAGA if you want to perform a distributed transaction.
