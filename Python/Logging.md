# Logging in Python

## Logging Library Entities

* Logger:

      First a logger filters a message based on its level.

* Handler:

      Then handler filters a message based on its level as well.

* Formatter:

      Each handler might have its own formatter
      which is applied before a message is sent to the handler's destination.

* Filter:

      Filter filters a message or enriches a message with new fields.

## Message Flow

1. Logger's severity level is checked.
2. Logger's attached filters are checked.
3. Logger's handlers' severity levels are checked.
4. Logger's handlers' filters are checked.
5. Handler's formatter formats a message.
6. A message is emitted to a destination.

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
