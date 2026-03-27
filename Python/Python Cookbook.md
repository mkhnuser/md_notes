# Python Cookbook by David Beazley

## Overview

Below I note my personal favorite recipes from the book.

## Chapter 1 - Data Structures and Algorithms

### Recipe 1.18

Use `._replace` method to create a brand-new named tuple with updated fields.

### Recipe 1.20

`collections.ChainMap` can be used to chain two dictionaries together;
references to original dictionaries is kept - no new dics are created.

### Chapter 1 Conclusion

The chapter contains a lot of info on dictionary manipulations & min / max & sorting.

## Chapter 2 - Strings and Text

### Recipe 2.14

Recall: `"a" "b"` results in concatenation of the two strings.
The behavior above can be especially tricky while working with sequences.

This recipe also contains a discussion on efficient text streaming
using generators and batching.

### Chapter 2 Conclusion

The chapter contains a lot of information on regular expressions
and text manipulation, HTML & XML including. This chapter also addresses
text tokenization, which is used in programming languages construction.

## Chapter 3 - Numbers, Dates, and Times

### Recipe 3.2

Perhaps, you should use `decimal` module only for the domain of finance
since `decimal` introduces a lot of overhead over plain `float` type.

A mind-blowing piece of code:

    nums = [1.23e+18, 1, -1.23e+18]
    sum(nums)
    0.0

### Chapter 3 Conclusion

The chapter discusses various discussions on
number precision, formatting, and representation.
It also contains useful information on `datetime` module.

## Chapter 4 - Iterators and Generators

### Recipe 4.5

Iterate a file in reverse.

### Recipe 4.15

Great usage of `heap.merge` function.

### Chapter 4 Conclusion

The chapter discusses `zip`, `reversed`, advanced iteration, and `itertools` module.
When faced with a complex iteration pattern, consult `itertools` documentation.

## Chapter 5 - Files and I/O

### Recipe 5.4

Discusses a gotcha when dealing with byte strings.

### Recipe 5.5

Discusses `io.StringIO` and `io.BytesIO`: these objects allow you to obtain a file-like
interface to a string.

### Recipe 5.8

Discusses how to iterate a file in chunks.

### Recipe 5.9

Discusses `memoryview` function.

### Recipe 5.10

Discusses `mmap` module and briefly discusses memory mapping concept as such.

### Recipe 5.21

A great example of usage of `pickle` module for Python object serialization,
which can later be stored in a DB, transferred over a network, or written to a file.

### Chapter 5 Conclusion

The chapter explains that bad file names or bad encoding can crush your program;
it also explains that an interaction with a file system in Python is built in layers,
and so you can hack it by accessing lower levels.

## Chapter 6 - Data Encoding and Processing

### Chapter 6 Overview

The chapter teaches you to work with JSON, XML, and DB Drivers.

## Chapter 7 - Function

### Recipe 7.5

A perfect usage of a sentinel `object()` pattern as the default parameter.
There is a distinction between passing no value and passing a value of `None`,
just like in many publisher-subscriber patterns, for example.

The recipe also explains that any default arguments are calculated at
a function definition time.

### Recipe 7.7

The recipe demonstrates how to capture variables while using `lambda` functions.

### Recipe 7.8

Greatly demonstrates the usage of `functools.partial`.

### Chapter 7 Overview

The chapter, toward the end, examines advanced usage of callback functions.

## Chapter 8 - Classes and Objects

### Recipe 8.3

Shows how to use a context manager to create a lazy network connection.
The potential to nest connections is also demonstrated.

### Recipe 8.5

Discusses name mangling.

### Recipe 8.6

Discusses `@property`.
The authors suggest to use `@property` to either add extra steps to an attribute access,
or to calculate an attribute on demand.

Wrapping something up in a `@property` decorator in expensive in terms of access time.
When you find yourself copying and pasting `@property`, consider using descriptors.

## Recipe 8.9

Provides a wonderful motivation for descriptor usage.

### Recipe 8.15

Discusses a Proxy pattern.

### Recipe 8.18

Discusses Mixins.

### Recipe 8.19

Discusses State Machine Implementation.

### Chapter 8 Overview

The chapter also discusses descriptors by providing numerous examples.
It also teaches you how to use `weakref` module to break cyclic references.

## Chapter 9 - Metaprogramming

### Recipe 9.2

Shows that a wrapped function can be accessed using `__wrapped__` dunder
on a resulting decorator.

### Chapter 9 Conclusion

An in-depth treatment of decorators in Python, as well as
does metaclasses treatment, `ast`, and bytecode disassembling.

## Chapter 11 - Network and Web Programming

### Recipe 11.1

An example of how to send the second request with the cookies from the first:

```
import requests


resp1 = requests.get(url)
resp2 = requests.get(url, cookies=resp1.cookies)
```

### Recipe 11.4

Discusses `ipaddress` package.

### Recipe 11.5

Discusses `wsgi` and `cgi`.

### Recipe 11.6

Discusses RPC implementation.

### Recipe 11.7

Discusses how to communicate between distributed Python Interpreters using `multiprocessing.connection` module.

### Recipe 11.10

Discusses `TLS` wrapper around a socket and certificates.

### Recipe 11.11

Discusses how to use `multiprocessing.Pipe` to communicate between separate processes.

### Recipe 11.12

Discusses how to implement your own event loop.

## Chapter 12 - Concurrency

### Recipe 12.1

The recipe explains that having a separate task which encapsulates
execution logic is better than inheriting from a `Thread` or a `Process`
since it decouples the execution task from the execution context.

### Recipe 12.3

Shows the usage of a sentinel `object()` for queue termination.
Important observation is that a sentinel is placed back to a queue.

The recipe also discusses communication between threads and explains that
`.size()`, `.full()`, `.empty()` methods of a queue are unreliable in multithreaded
environments.

### Recipe 12.4

Provides a great example of usage for `RLock` and `Semaphore`.

### Recipe 12.5

Discusses how to avoid deadlocks and solve The Dining Philosophers Problem.

### Recipe 12.6

Shows how to use `threading.local` to create multithreaded TCP clients.

### Recipe 12.7

Explains why it is important to put an upper limit on the number of threads
in a thread pool.

### Recipe 12.8

Discusses important considerations when you use a process pool.

### Chapter 12 Conclusion

The chapter discusses threading, synchronization primitives & pub / sub architectures.
It also teaches you how to implement your own event loop using generators.

### Chapter 13 - Utility Scripting and System Administration

### Recipe 13.6

Demonstrates the usage of `subprocess` module for external command execution.

### Chapter 13 Conclusion

The chapter discusses how to limit CPU resources, open a web browser, and
other common system administration tricks.

## Chapter 14 - Testing, Debugging, and Exceptions

### Recipe 14.9

Recall that you can use `raise ... from None` syntax to break exception chain.
The usage of `raise ... from ...` makes your intention clear: you declare that
you raise one exception from another.

### Chapter 14 Conclusion

The chapter contains information on `unittest` mocking, debugging, basic profiling.
It also addresses common optimization techniques.

## Chapter 15 - C Extensions

### Chapter 15 Conclusion

The chapter title is pretty self-explanatory.
