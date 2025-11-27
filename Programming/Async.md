# Async

When you use asyncio.create_task, it acts as FIFO queue:
the tasks are executed in the background in the order you've defined them.
