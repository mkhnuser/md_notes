# System Requirements

## System Requirements Gathering

Be sure to gather requirements explicitly, not implicitly.
What is obvious for you will not be obvious to others.
A design document should explicitly state what's expected from the system.

### Functional vs Non-Functional Requirements

Functional: what do you expect as a user?

Non-Functional:

* How do you make system highly available, scalable, responsive?
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

Non-Functional Requirements

CAP-Analysis:

* Availability - no one wants to use a social net that is unavailable.
* Partition Tolerance.
* Inconsistency is allowed: it is OK if a user sees an a slightly outdated profile of someone else.

##### URL Shortener

Functional requirements:

* An ability to post a long link and obtain a small one;
* An ability to access the shortened resource through a browser.
* Delete an obtained short link;

Non-Functional Requirements

CAP-analysis:

* Availability - users have to be able to access a resource which is associated with a short URL.
* Partition Tolerance.
* Inconsistency is possible: it is OK if a user accesses an expired link.

##### Search Autocomplete

Functional Requirements:

* An ability to type text;
* An ability to see ranked search results;
* An ability to choose any search result.

Non-Functional Requirements:

* High Speed of Searching;
* Relevance of Results based on how popular they are;
* Optionality - if this service fails, it should not affect the main service.

##### Online File Storage

Functional Requirements:

* An ability to create an account;
* An ability to upload any file;
* An ability to download a file;
* An ability to view files in my account;

Non-Functional Requirements:

CAP-Analysis:

* Availability - Partition Tolerance - Inconsistency is possible.
I allow inconsistency since it seems to me that
this service has much more read importance than write importance.

* Restrict File Size upload;
* Restrict Storage Capacity per a user Account.
* ACID-like handling of a file.

##### Messanger

CAP-Analysis:

* ? Consistency - you want to have the same chats on all devices.
* Partition Tolerance.
* Unavailability might be the case if you want to achieve consistency.

##### X

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

##### Netflix

Low latency.

##### Restaurants Nearby

Fast Search.
Locality.

##### A Taxi Service

Driver / user separation.
Locality.
High Availability.
Low waiting time.

##### Video-streaming Service

### Load on a System Assessment

Load on a system can be calculated based on these metrics:

* User Load;
* Network Load;
* Computational Load;
* Storage Space.

#### User Load

Consider this:

* MAU - Monthly Active Users;
* DAU - Daily Active Users;
* How much content will be generated in the next 5 years?
* How much content does a user generate per day?
* Calculate READ / WRITE Ratio.

Calculate this:

* RPS;
* QPS (Search Engine, DB);
* CPS (Connections Per Second);
* How many connections are open simultaneously?

      Recall what c10K problem, c1M problem means.

* Network Load (mbps, gbps);
* Storage Space Requirements (TB);
* Calculate Server Costs;
* https://en.wikipedia.org/wiki/Web_server#Performance_metrics

#### Network Load

To calculate network load, consider these metrics:

1. Traffic Load (mbps, gbps);
2. Number of open connections (perhaps less significant).

On average, to transfer 1GB of traffic, you have to pay $0.1.
One web server instance can handle 100 thousand connections.
You should know how much traffic can be transferred per second.

There are various performance metrics one can assess:

* https://en.wikipedia.org/wiki/Time_to_first_byte
* Bit Rate and Resolution for video-streaming.
* Video: https://medium.com/tinder/taming-video-delivery-through-http-live-streaming-5a4d6e543c85
* General SRE book: https://sre.google/sre-book/service-level-objectives/

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

* You should know their read / write speed and cost.
* One server might have up to 1TB of RAM, up to 50TB of SSD, up to 200TB of HDD.
* You should know L1 cache access time, RAM access time, etc.
* Average Failure Rate (AFR) of a storage device is around 1 percent.
* Information should be replicated across multiple disks.
