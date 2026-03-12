# Closures

In Python, you have `nonlocal` and `global` keywords.
Understand: you can always mutate mutable data types: lists, dicts, etc.
You only need `nonlocal` or `global` to reassign immutable objects.

## Closures without nonlocal & global

```
def new_collection(initial_docs: list[str]) -> Callable:
    docs_copy = initial_docs.copy()
    def add_doc(doc: str) -> list[str]:
        docs_copy.append(doc)
        return docs_copy
    return add_doc
```

Note that in the example above, you don't need the keyword since you
are dealing with a mutable type - list.
