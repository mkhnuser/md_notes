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

### OLAP, OLTP, HTAP

* OLAP = Online Analytical Processing.
* OLTP = Online Transactional Processing.
* HTAP = Hybrid Transactional / Analytical Processing.

Usually, there is a lot of OLTP requests, but few OLAP requests.
However, OLAP requests generate a lot of load, whereas OLTP don't.
Because of this, it makes sense to use separate databases based on these types of requests.

## CAP theorem and databases

### CA systems

Relational DBs are Consistent and Available, they are not Partition Tolerant by design.
This implies that these systems are often vertically scaled, but not horizontally.

### CP systems

HBase, MongoDB, Redis.

### AP systems

Cassandra, CouchDB, Dynamo.

# Common Large Files Hashing

Suppose multiple users upload the same huge popular file.
Then you can hash this file and by hash access this file in your DB.
