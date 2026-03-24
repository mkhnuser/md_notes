# Functions

## *args, **kwargs

Note that in a function, `*args`, `**kwargs` are tuple and dict, respectively.
Whereas, inline `*args` is a list:

```
a, *rest = [1, 2, 3]
print(type(rest))  # list
```

## Positional-only and keyword-only arguments

```
def read(fp, /, arg, *, auto_close):
    pass
```

In the example above: `fp` is positional only, `arg` can be any,
and `auto_close` is keyword-only.

Note the usage of only one star.

## Default Arguments

It's a well-known bug to do something like this in Python:

```
def f(arg=[]):
    pass
```

One should use `None` instead or even `object()` instead.

Also see the following:

```
x = 42


def f(arg=x):
    print(x)


x = -1
f()
```

In the example above, in the function, x will still refer to 42,
since default arguments are only initialized once.

Refer to the Python Cookbook notes you've written.

## LEGB rule variable lookup is dynamic

Suppose only a function is defined:

```
def f():
    print(i)
```

You can then do:

```
for i in range(5):
    f()
```

The code above works since LEGB rule is dynamic for variable lookup.
There is a strong difference between a lookup and modification.

## Decorators

### Parametrized Decorators

The code below:

```
@trace(sys.stdout)
def func(a, b):
    pass
```

Is equivalent to:

```
deco = trace(sys.stdout)
func = deco(func)
```

### Multiple Decorators

The code below:

```
@a
@b
@c
def func():
    pass
```

Is equivalent to:

```
func = a(b(c(func)))
```

As a consequence, the order of decorators matters.

## Links

https://www.youtube.com/watch?v=3fE_08eXyE4&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=2
https://www.youtube.com/watch?v=h_B3O5jWMi4&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=3
Python Cookbook.
