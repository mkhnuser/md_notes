# Async

## Hierarchy

`Future` inherits from `Awaitable`, `Task` inherits from `Future`.
`Coroutine` inherits from `Awaitable`.

## Tasks

### Execution Order

When you use `asyncio.create_task`, it mostly acts as a queue:
the tasks are usually executed in the order you've instantiated them.

https://docs.python.org/3/howto/a-conceptual-overview-of-asyncio.html#a-conceptual-overview-of-asyncio

### Task Garbage Collection Problem

Keep references to tasks, otherwise they can be garbage collected.

### Task Groups

Task Groups allow you to automatically await the tasks you spawned.

https://docs.python.org/3/library/asyncio-task.html#coroutine

### Awaiting a task vs awaiting a coroutine object

"Unlike tasks, awaiting a coroutine does not hand control back to the event loop!"

https://docs.python.org/3/howto/a-conceptual-overview-of-asyncio.html#a-conceptual-overview-of-asyncio

## Async REPL

`python -m asyncio` command can be used to access an asyncio REPL.

https://docs.python.org/3/library/asyncio.html

## Logging

Don't forget to do logging in a separate thread using `QueueHandler` and `QueueListener`.
