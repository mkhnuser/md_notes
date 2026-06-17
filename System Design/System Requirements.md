# System Requirements

## System Requirements Gathering

Be sure to pin down system requirements precisely.
What is obvious for you will not be obvious to others.
A design document should explicitly state what's expected from the system.

## Functional & Non-Functional Requirements

Functional: what do you expect as a user? What functions does your application provide?

Non-Functional:

* How do you make system highly available, scalable, responsive?
* Do you really need to make it highly available, scalable?
* What delay can you afford between a user action and a result display?
* How does CAP theorem apply to a system?

## Examples

### Social Network

Functional requirements:

* Create an account;
* Add to a friend list;
* Write a Direct Message;
* Create a Public Channel;
* Create Public Posts;

Non-Functional Requirements:

CAP-Analysis:

* Availability - no one wants to use a social net that is unavailable.
* Partition Tolerance.
* Inconsistency is allowed: it is OK if a user sees a slightly outdated profile of someone else.

### Online File Storage

Functional Requirements:

* An ability to create an account;
* An ability to upload any file;
* An ability to download a file;
* An ability to view files in my account;

Non-Functional Requirements:

* Restrict File Size upload;
* Restrict Storage Capacity per a user Account.
* ACID-like handling of a file.

### X

CAP-Analysis:

* Availability;
* Partition Tolerance;
* Inconsistency is possible for not-so-popular users.

Functional Requirements:

* Post text;
* Post short videos and audio messages;
* Reply to other users.

Non-Functional Requirements

* High Availability is desired;
* Reliability - if a user posts something, it has to be available for ever (well, at least for some long time).
* Instant Display of the Feed.

## Load on a System Assessment

Load on a system can be calculated based on these metrics:

* User Load;
* Network Load;
* Computational Load;
* Storage Requirements.

### User Load

Consider this:

* MAU - Monthly Active Users;
* DAU - Daily Active Users;
* How much content will be generated in the next 5 years?
* How much content does a user generate per day?
* Calculate READ / WRITE Ratio.

When you do the calculation, use powers of ten to simplify your calculations.

### Network Load

To calculate network load, consider these metrics:

1. Traffic Load (mbps, gbps);
2. Number of open connections (perhaps less significant).

On average, to transfer 1GB of traffic, you have to pay $0.1.
One web server instance can handle 100 thousand connections.
You should know how much traffic can be transferred per second.

There are various performance metrics one can assess:

* https://en.wikipedia.org/wiki/Time_to_first_byte
* Bit Rate and Resolution for video-streaming.

### Computational Load

Estimate how much RPS one instance can handle.
RPS capacity: https://www.techempower.com/benchmarks/#section=data-r23&l=zijzen-pa7&test=update

Ask this:

* How much load can one cloud instance handle based on the benchmark?
* How many instances do you need to buy?

### Storage Space

There the three main types of storage devices:

1. HDD;
2. SSD;
3. RAM.

* You should know their read / write speed and cost.
* Roughly, one server might have up to 1TB of RAM, up to 50TB of SSD, and up to 200TB of HDD.
* You should know L1 cache access time, RAM access time, etc.
* Average Failure Rate (AFR) of a storage device is around 1 percent.
* Information should be replicated across multiple disks (RAID).
