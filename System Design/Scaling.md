# Scaling

## Load Balancer

### Balancing Strategies

A load balancer might choose a machine with least connections if your goal is to
not exceed network bandwidth, but you usually use consistent hashing strategy.

## Data Scaling

### Shards

As the load on your system increases, you might want to use database shards
to distribute the load across multiple database instances. However,
this approach has at least the following disadvantages:

* Inability to perform SQL-Joins.
* Almost all Relational Databases can't validate the foreign key references to external nodes.
* If you use consistent hashing and you need to change a hash function,
you need to redistribute your data across shards.

### Redundancy and Replication

Redundancy refers to a fact that one instance might fail and so one needs
to have a standby instance which is ready to assume responsibility.

Replication assumes that you copy data to a standby instance and
you keeps this instance in sync with the main instance.
