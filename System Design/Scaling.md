# Scaling

## Load Balancer

### Types of Load Balancing

* Client-side load balancing (your application code);
* Server-side load balancing (nginx, apache, etc).

### Balancing Strategies

#### Random

Proxy requests randomly.

#### Round Robin

Proxy requests in a cyclic nature.

#### Weighted Round Robin

Proxy requests in a cyclic nature, but assign a higher priority to some server.

#### Sticky Sessions

If you store user's session on a server,
you want to route a particular user's traffic on this server.
To achieve this, consider using consistent hashing.

#### Least Connection, Least Response Time, etc.

Proxy to servers with least connection, response time, etc.

### L4 and L7 balancing

* L4 balancing just proxies all the traffic;
* L7 allows you to proxy the traffic based on some L7-level metric (HTTP cookies, HTTP Header, etc.)

### DNS and geoDNS Balancing

Place a load balancer behind a DNS record.

### Health Checks

A load balancer can perform health checks against servers.
Alternatively, k8s, for example, can be used for this.

## Message Brokers

Message brokers allow:

* Asynchronous communication;

      You don't need to wait for some tasks.

* Decouple your services and hence allow easier scaling;
* Reliability;

      If one service dies, a message broker will still contain a message you've sent.

* Data Flow.

You should be ready to handle message duplicates. There are
various strategies for this:

* At least once;
* At most once;
* Exactly once.

Consider the usage to the idempotency key to handle a message only once.

You can also put a message broker in front of database:
if a database fails, you won't lose a message.

## Data Scaling

### Shards

As the load on your system increases, you might want to use database shards
to distribute the load across multiple database instances. However,
this approach has at least the following disadvantages:

* Inability to perform SQL-Joins.
* Almost all Relational Databases can't validate the foreign key references to external nodes.
* If you are to change a hash function, you need to redistribute your data across shards.

### Consistent Hashing

Given many shards of data, we need to route the request to a particular shard
based on some field in this request. This is where classical (hashing + mod) might fail
if you want to add a new shard. To solve this problem, you introduce consistent hashing.

### Redundancy and Replication

Redundancy refers to a fact that one instance might fail and so one needs
to have a standby instance which is ready to assume responsibility.

Replication assumes that you copy data to a standby instance and
you keeps this instance in sync with the main instance.
