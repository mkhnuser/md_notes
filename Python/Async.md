# Async

## Hierarchy

`Future` inherits from `Awaitable`, `Task` inherits from `Future`.
`Coroutine` inherits from `Awaitable`.

## Tasks

### Execution Order

When you use `asyncio.create_task`, it mostly acts as a queue:
the tasks are usually executed in the order you've instantiated them.

https://docs.python.org/3/howto/a-conceptual-overview-of-asyncio.html#a-conceptual-overview-of-asyncio

### Task Groups

Task Groups allow you to automatically await the tasks you spawned.

https://docs.python.org/3/library/asyncio-task.html#coroutine

### Awaiting a task vs awaiting a coroutine object

"Unlike tasks, awaiting a coroutine does not hand control back to the event loop!"
As such, an event loop is an abstraction which is introduced by the `asyncio` library.

https://docs.python.org/3/howto/a-conceptual-overview-of-asyncio.html#a-conceptual-overview-of-asyncio

### Cancellation

When you cancel a task `t`,
`asyncio.CancelledError` is raised inside `t` at an available `await` statement.

Once a task `t` has been cancelled,
an `asyncio.CancelledError` exception is raised when you do `await t`
if `t` has not suppressed `asyncio.CancelledError`.

## Async REPL

`python -m asyncio` command can be used to access an asyncio REPL.

https://docs.python.org/3/library/asyncio.html

## Logging

Do logging in a separate thread using `QueueHandler` and `QueueListener`
in order to not block an event loop.
