# Async

## Tasks

When you use asyncio.create_task, it acts as FIFO queue:
the tasks are executed in the background in the order you've defined them.

Remember that the executing happens only after await has been hit.
Obviously, keep references to tasks. Otherwise, they might be garbage collected.
