# Exception

## except can accept an expression

The code below ignores swallows the exception if it happens two times in a row.

```
try:
    do_something()
except Exception as e:
    try:
        do_something_else()
    except type(e):
        pass
```

## Exception Hierarchy

Consider defining exception hierarchy for your library.

## Exception Groups

# TODO: Investigate this concept.

## Exception Chaining

Note that you can break an exception chain by using `raise ... from None`.
See Python Cookbook, Recipe 14.9.

The usage of `raise ... from ...` makes your intention clear: you declare that
you raise one exception from another.

## Links

https://www.youtube.com/watch?v=_vxcRfjyfgk&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=7&t=6s
