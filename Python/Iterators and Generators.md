# Iterators and Generators

## Overview

Observe: `__iter__` can be a generator function itself:

```
class LinkedList:
    def __init__(self):
        self.head = None

    def __iter__(self):
        current = self.head
        while current is not None:
            yield current
            current = current.next
```
