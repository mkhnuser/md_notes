# Responsiveness

The problem: you want to make your system more responsive (fast).

## Cache

Cache can be used at any level of your system.
Use 80 / 20 rule: 20 percent of data caching give you 80 percent of responsiveness increase.
You might want to store the most frequently accessed cache in memory,
but at the same time use SSD or HDD for less popular cache.

## Cache Invalidation

Sometimes you want to invalidate cache.
Cache invalidation refers to a fact that cache might become stale
and therefore does not represent the state of your system.

To invalidate cache, you might:

* Write both to DB and cache.
* Write to DB first and then sync cache with DB.
* Write to cache first and then sync DB with cache.

## Cache Rotation

To reclaim cache space you might want to consider LRU or LFU strategies.

## What one might cache?

* Requests to other services.
* Requests to DB or other storage.
* Web pages.

## CDN

Content Delivery Network allows you to speed up resource acquisition process.

## Indexes

Consider the usage of indexes to increase responsiveness.

## Connection types

Consider using the appropriate connection type for your service:
websocket, HTTP request-response, etc.
