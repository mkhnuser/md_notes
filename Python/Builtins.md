# Builtins

## Builtin Functions

These notes highlight useful builtins.

* `zip` & `zip_longest`;
* `reversed`:

      Implement __reversed__ dunder,
      or provide an object whose size can be determined.

* `open`:

      By default, files are open in a universal newline mode.
      Possible open flags:
            r, w, a;
            r+ or w+ - both reading and writing;
            x - exclusive access: open a file for write operations
            if it does not exist. If it exists, raise an exception.

* `memoryview`:

      MemoryView allows you to create a slice of a buffer without copying.
      Any further modification of the obtained memory view will modify the original buffer.

## Builtin Types

### Lists

When you do as follows:

```
matrix = [[0]] * 2
```

You actually copy a reference to the same mutable object.
Use list comprehensions to overcome this issue.

There is no problem doing something as follows: `[None] * 42`,
since `None` is an immutable singleton.

### Sets and Frozensets

You can use set intersections to exclude curtain keys from a dict:

```
keys_to_include = {"a", "b", "c"}
d = {k: outer_dict[k] for k in (outer_dict.keys() & keys_to_include)}
```

Python Cookbook, Chapter 1, contains a lot of examples as the one above.

If you want to include sets in other sets, for example, consider using `frozenset`.

### Dictionaries

A captain informs: you should not modify a mutable sequence while iterating over it.
Instead, iterate over a copy:

```
for k in set(d):
    del d[k]
```


## Links

Python Cookbook, Chapter 1 especially.
https://www.youtube.com/watch?v=vne1p3huhew&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=6
