# Parallelism

## Processes

Processes don't see other processes':

* Virtual Address Space;
* Pointer to the currently running instruction;
* Call Stack;
* Resources: file descriptors, locks, etc.

## Threads

You use threads usually when you want to share a common resource.
In Python, threads are real operating system threads, they are managed by an OS.

## Inheriting from threading.Thread

Perhaps, instead of inheriting from the `threading.Thread`,
you want to pass an object which represents a task of some kind.
This object encapsulates all the execution logic and can be easily terminated:

```
class Task:
    def __init__(self):
        self.running = True

    def terminate(self):
        self.running = False

    def run(self):
        while self.running:
            pass
```

## Naming Threads

Perhaps, you want to name your threads for debugging purposes.

## Cancelling Threads

Python does not provide interfaces for cancelling threads since,
internally, threads can hold resources.

Consider using a task object for graceful execution cancellation.

## Synchronization Primitives

### Lock

Allows you to control the critical sections.
Be aware that lock can be released by any thread,
not only the thread which acquired it.

Always use context managers with locks.

### RLock

The same as `Lock` but can be acquired multiple times by the same thread.

### Condition

Be aware of spurious wakeups.

## queue module

`queue` module is threadsafe.
Use `.join()` and `.task_done()`.

## `concurrent.futures` package

One can use `Future` object to obtain a result from a thread.

## GIL

Global Interpreter Lock does not prevent I/O operations or C-level code execution to run concurrently using threads,
GIL only locks parts which translate into Python Bytecode.

## Links

Python Cookbook.
https://www.youtube.com/watch?v=nR8WhdcRJwM&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=13&t=198s
