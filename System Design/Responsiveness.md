# Responsiveness

## Cache

Roughly, if you cache 20% of data, you get 80% increase in responsiveness.

## Why do you cache?

* Increase response time;
* Decrease load on other external services;

## But what do you cache?

* Requests to other services.
* Requests to DB or other storage.
* Web pages;
* Requests, based on a set of parameters.

## Cache Strategies

There are various cache strategies one can use.

## Cache Invalidation

Sometimes you have to invalidate stale useless data:

* TTL invalidation;

      Remember about the thundering herd problem:
      always create TTL with some jitter.

* Invalidation by event;
* Invalidation by versioning;
* Invalidation by taging.

## Cache Rotation

To reclaim cache space you might want to consider LRU, LFU, etc.

## CDN

Content Delivery Network allows you to speed up resource acquisition process.

## Database Indexes

Consider the usage of indexes to increase responsiveness.

## Connection types

Consider using the appropriate connection type for your service:

* Websocket;
* HTTP request-response;
* Server-sent events.
