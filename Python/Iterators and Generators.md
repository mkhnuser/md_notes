# Iterators and Generators

## Observations

* Observe: `__iter__` can be a generator function itself:

      class LinkedList:
          def __init__(self):
              self.head = None

          def __iter__(self):
              current = self.head
              while current is not None:
                  yield current
                  current = current.next

It makes sense, since `__iter__` invocation returns a generator object,
which is in turn an iterator, and so `__iter__` contract of returning an iterator holds.

* Observe: `__iter__` can return `iter(iterable)`.

It makes sense, since `iter` function returns an iterator.

* Observe: files in Python are iterators.

## Iterable, Iterator, Generator

### __iter__ dunder method

`__iter__` dunder method must return an iterator.

### Iterable

Iterable is an object which returns its members one at a time.
Iterable might implement `__iter__` to return an actual iterator.

### Iterator

1. Iterator: `__iter__` + `__next__`.

Iterator must implement `__iter__` method which returns
an iterator object itself, which in turn contains `__next__`
method which returns a member of the iterator.

In this sense, every Iterator is also an Iterable.

Once `StopIteration` exception is raised by `__next__`,
every subsequent call to `__next__` has to raise `StopIteration`.

2. Iterator: `__getitem__`.

Iterator might also be implemented implicitly using `__getitem__`.
`__getitem__` is invoked when you use `obj[1]` syntax.

### in and not in, __contains__

In Python, `in` and `not in` are implemented using `__contains__`.
The method `__contains__` is defined automatically for an iterator;
it sequentially scans your sequence.

### Generator

Generator is defined by using `yield` or `yield from` in a function body.

There are:

1. Generator Function;
2. Generator Object.

Every Generator is an Iterator.
Every Generator is Iterable.

`next` function will:

1. Resume a generator body until it hits the `yield` statement;
2. Return the yield value.
3. Stop further execution until next `next` is invoked.

### send, throw, close

Prior to using `send` method of a generator object,
you have to hit the `yield` by using `next` on the generator object.

`send(None)` is the same as `next`.
`throw(ValueError, 42)` throws an exception at the current `yield` statement.
`close` raises `GeneratorExit` at the current yield statement.

### return in Generator Function Body

`return 42` raises `StopIteration(42)`.
Note that you can't catch `return`, whereas you can catch `StopIteration`.

## Async Iterators

To implement async iterators, implement a sync `__aiter__` and an async `__anext__`.
After that, you can use `async for` syntax to iterate over an async iterator.
The iteration stops when `StopAsyncIteration` is raised from `__anext__`.

https://realpython.com/python-async-iterators/

## References

Python Cookbook by David Beazley.
https://www.youtube.com/watch?v=snJhrhD9Sg8&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=8
https://www.dabeaz.com/coroutines/
