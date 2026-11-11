# Resilience

## Idempotency Key

When you don't want to perform some non-idempotent operation more than once,
you might want to use an idempotency key.

For example, you wouldn't want to book the same flight twice.
Similarly, you wouldn't want to pay for a service twice.

! Generate the key only on the client.

## Timeouts

Specify timeouts for all your requests.

## Session-level error handling

Handle errors at the request session level too.

## Retries

Implement retries with jittery.

## Circuit Breaker

https://learn.microsoft.com/en-us/azure/architecture/patterns/

## Backpressure

https://medium.com/@jayphelps/backpressure-explained-the-flow-of-data-through-software-2350b3e77ce7

## Graceful Degradation

You might want to disable some services of your system
to preserve other critical components of your system.

## Transaction Outbox

You can use transaction outbox if you want to guarantee that
a message will be published to a queue.

## Transaction Inbox

Similar to the outbox.
