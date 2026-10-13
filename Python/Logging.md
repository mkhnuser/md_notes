# Logging in Python

## Message Flow

A rough message flow is as follows:

1. Logger's severity level is checked.
2. Logger's attached filters are checked.
3. Logger's handlers' severity levels are checked.
4. Logger's handlers' filters are checked.
5. Handler's formatter formats a message.
6. A message is emitted to a destination.

Obviously, there might be multiple handlers, for one logger.

## Message Propagation

When a message propagates,
it ignores the parent logger's set level and the parent logger's filters.

It will only respect the parent logger's handler's set level and the current logger's level.

## Structured Logging

Instead of creating one text message, consider the usage of structured logging.

## Logger Creation

A logger is created only once: subsequent `.getLogger` invocations
will result in obtaining the same logger.

## How do you set up logging in your project?

Perhaps one should create a separate logger per file,
and only configure the root logger to handle messages.
This way, messages will be propagated to the root logger and handled there.

## How do you log exceptions that occur?

Consider the usage `logger.exception` or `exc_info=True` + a JSON log formatter.

## Non-blocking logging

Remember to use `QueueHandler` and `QueueListener` so that your event loop is not blocked.

## Links

https://www.youtube.com/watch?v=jF_XglX0JgM&t=5620s
