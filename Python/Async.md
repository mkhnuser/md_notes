# Async

## Tasks

### Execution Order

When you use `asyncio.create_task`, it acts as FIFO queue:
the tasks are executed in the order you've defined them.

### Task Garbage Collection Problem

You should always keep references to tasks,
otherwise they might be garbage collected, which leads to bugs.
