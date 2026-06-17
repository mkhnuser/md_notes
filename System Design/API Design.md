# API Design

## HTTP Rest API

### Overview

One of the biggest advantages of having API is loose coupling: you don' need to
know the internal implementation of a service you are communicating with.

### Asynchronous Responses

Sometimes a client requests some long-running operation. In this case, you might
return a response which contains a URI to the status endpoint: /api/v1/status/<id>.

### Partial Responses

Partial Responses may be used to stream large files.
https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design

## SOAP

All information is passed in an XML document.

## RPC

Some procedures access external resources over HTTP (usually).

## Under and Over Data Fetching

Make sure not to send more data than necessary.
That where GraphQL or pagination comes into play.

## GraphQL

A client postulates which data it needs.

## Polling

Every `n` seconds a client sends a request to a server to see if data is available.

## Webhook

A client sends a request which contains a callback URL to which data should be sent.

## API Performance

* You can compress data you send over a network.
* Cache data client-side.

## Idempotency Key

When you don't want to perform some non-idempotent operation
more than once (POST-request, for example), you might want to use an idempotency key.

For example, you wouldn't want to book the same flight twice.

! Generate the key only on the client.

## Timeouts

Specify timeouts for your requests.

## Session-level error handling

Handle errors at the request session level too.

## Retries

Implement retries with jittery.

## Design Patterns

Consider the usage of a Circuit Breaker.

https://learn.microsoft.com/en-us/azure/architecture/patterns/

## Backpressure

https://medium.com/@jayphelps/backpressure-explained-the-flow-of-data-through-software-2350b3e77ce7

## Graceful Degradation

One might want to disable some services of your system
in order to preserve other critical components of your system.
