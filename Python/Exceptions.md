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

## Links

https://www.youtube.com/watch?v=_vxcRfjyfgk&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=7&t=6s
