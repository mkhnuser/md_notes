# In-Memory Stores

## Overview

The primary advantages of using in-memory store is to have your application stateless.
Examples of in-memory stores are:

* Postgres Hstore;
* Memcached - the simplest one;
* Redis - the most sophisticated.

## Redis

One can set a time-to-live for a key (TTL).

## Thundering Herd Problem

Once your cache is stale, your DB might experience a staggering number of queries.
