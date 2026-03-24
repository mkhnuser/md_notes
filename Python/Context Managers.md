# Context Managers

## Overview

The primary advantage of using a context manager is to carefully
initialize a resource on demand.

## Exceptions within the given context

If an exception occurs, exception type, exception value, and traceback
are passed to the `__exit__`. If there is no exception, these values are `None`s:

```
def exit(self, exc_type, exc_value, tb):
    pass
```

## Return truthiness of the __exit__ method

If `__exit__` returns a falsy value, the exception which has occurred (if any)
is raised. However, if `__exit__` returns a truthy value,
the exception is not raised and the program execution continues after the `with` block.

## Async Context Managers

Implement `__aenter__` and `__aexit__` coroutine dunders to implement an async context manager.
They have the same signature, and you can use `await` inside them.

https://stackoverflow.com/questions/37433157/asynchronous-context-manager

## Links

Python Cookbook, Chapter 8.
https://www.youtube.com/watch?v=_vxcRfjyfgk&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=7&t=6s
