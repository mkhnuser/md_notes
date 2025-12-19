# Database Choice

When you make a database choice, consider CAP theorem first.

## CA systems

Relational DBs are Consistent and Available, they are not Partition Tolerant by design.
This implies that these systems are often vertically scaled, but not horizontally.

## CP systems

HBase, MongoDB, Redis.

## AP systems

Cassandra, CouchDB, Dynamo.

# Common Large Files Hashing

Suppose multiple users upload the same huge popular file.
Then you can hash this file and by hash access this file in your DB.

## Examples of DB Usage

### Key-value

* Sessions;
* Cart in an online shop.

### Wide-column

* Analytics;
* Sparse data.

### Document-oriented

* JSON Blobs;
* Catalogs.
