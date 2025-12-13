# System Requirements

## System Requirements Gathering

Be sure to gather requirements explicitly, not implicitly.
What is obvious for you will not be obvious to others.
A design document should explicitly state what's expected from the system.

### Functional vs Non-Functional Requirements

Functional: what do you expect as a user?

Non-Functional: 

* How do you make system highly available, scalable?
* Do you really need to make it highly available, scalable?
* What delay can you afford between a user action and a result display?
* How does CAP theorem apply to a system?

#### Examples

##### Social Network

Functional requirements:

* Create an account;
* Add to a friend list;
* Write a Direct Message;
* Create a Public Channel;
* Create Public Posts;

##### URL Shortener

Functional requirements:

* An ability to post a long link and obtain a small one;
* An ability to access the resource through a browser.
* Delete an obtained short link;

##### Search Autocomplete

##### A Taxi Service

##### Video-streaming Service

### Load on a System Assessment

Load on a system can be calculated based on these metrics:

* Number of users;
* Network Load;
* Computational Load;
* Storage Space.

#### Number of users

Consider this:

* MAU - Monthly Active Users;
* DAU - Daily Active Users;
* How much content will be generated in the next 5, 10 years?
* How much content does a user generate per day?
* Calculate READ / WRITE Ratio.

* How many requests per second does a particular instance have to handle (RPS)?
* How many connections are open simultaneously?
* Network Load (mbps, gbps);
* Storage Space Requirements (TB);
* Calculate Server Costs.

#### Network Load

To calculate network load, consider these metrics:

1. Traffic Load (mbps, gbps);
2. Number of open connections (perhaps less significant).

One instance can handle ~100k simultaneous connections.
On average, to transfer 1GB of traffic, you have to pay 0.1 dollar.

#### Computational Load

Investigate: https://www.techempower.com/benchmarks/#section=data-r23&l=zijzen-pa7&test=update
You should analyze what you expect from your system: is it read or write heavy or neither?
Based on this analysis you should estimate RPS that one instance can handle.

Ask this:

* How much load can one cloud instance handle based on the benchmark?
* How many instances do you need to buy?

#### Storage Space

There the three main types of storage devices:

1. HDD;
2. SSD;
3. RAM.

You should know their read-write speed and cost.
One server might have up to 1TB of RAM, up to 50TB of SSD, up to 200TB of HDD.
You should know L1 cache access time, RAM access time, etc.
Average Failure Rate (AFR) of a storage device is around 1 percent.
