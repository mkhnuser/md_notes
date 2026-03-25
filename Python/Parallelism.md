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

## Inheriting from a `Thread` or a `Process`

Instead of inheriting from a `Thread`,
you want to pass an object which represents a task.
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

Also, the usage of task decouples the execution task from the execution context:
you can execute a task within any context: multithreading or multiprocessing.
Also, the testing is easier.

## Naming Threads

Perhaps, you want to name your threads for debugging purposes.

## Cancelling Threads

Python does not provide interfaces for cancelling threads since,
internally, threads can hold resources.

Consider using a task object for graceful execution cancellation.

## Synchronization Primitives

### Lock

Be aware that lock can be released by any thread, not only the thread which acquired it!

### Condition

Be aware of spurious wakeups.

## queue module

`queue` module is thread safe.

Don't forget to use `.join()` and `.task_done()`.

The reason for the `.join()` usage is because it's not enough to check the queue size
to determine whether the program should be finished or not:
a thread which got the last task off a queue
might still be processing the task.

## `concurrent.futures` package

One can use `Future` object to obtain a result from a thread.

## Logging

Don't forget to do logging in a separate thread using `QueueHandler` and `QueueListener`.

## `threading.local`

Use `threading.local` to store information specific to a thread -
no other threads can see it.

## Multiple Processes

In Python, when you spawn a separate process, you spawn a separate Python Interpreter.
To pass data to another process, it has to be first serialized, so you should be aware
of the associated overhead.

Prefer pure functions for the ease of parallelization.

## Links

Python Cookbook, Chapter 12.
https://www.youtube.com/watch?v=nR8WhdcRJwM&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=13&t=198s
