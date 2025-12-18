# High-Level Design

High-Level design is a general design of your system.
Once high-level design is done, you can expand the design further.

## Metadata and Data Separation

You should store metadata and data separately for large files / blobs.

* Data: photos. Metadata: Creation Time, Update Time.
* Data: movies. Metadata: Actors, Movie length.
* Data: large text blob. Metadata: IP of a user who created it.
