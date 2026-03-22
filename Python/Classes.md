# Classes

# Lecture 1 starts here

## Class Attributes

There is a strong separation between an instance attributes
and class attributes:

```
class FooBar:
    pass


FooBar.attr = 42
```

In the example above, 42 will be shared among all instances.
One should exercise special care when sharing mutable objects.

Note that you should use `__class__` to access a class:

```
class FooBar:
    just_list = []
    def __init__(self):
        self.__class__.just_list.append(1)
```

The code above makes your code less fragile.

## Class dunder attributes

`FooBar.__bases__` returns a tuple of all base classes of a given class.
`FooBar.__class__` returns a `type`.

## Instance dunder attributes

`foobar.__dict__` returns a dict of all attributes of a given object.
When you set, update, or delete attributes of an instance,
you modify the underlying dict:

```
foobar.attr = 42
```

Is the same as:

```
foobar.__dict__["attr"] = 42
```

The same logic applies to deletion and update.

`vars(foobar)` is the same as `foobar.__dict__`.

## __slots__ dunder class attribute

One can define `__slots__` in order to not create a `__dict__` for an instance.
Therefore, `__slots__` is memory efficient.

`__slots__` is useful when you have a finite number of attributes:

```
class Point:
    __slots__ = ["x", "y"]

    def __init__(self, x, y):
        self.x = x
        self.y = y
```

```

>>> p = Point(1, 2)
>>> p.x
1
>>> p.y
2
>>> p.z = 42
Traceback (most recent call last):
  File "<python-input-16>", line 1, in <module>
    p.z = 42
    ^^^
AttributeError: 'Point' object has no attribute 'z' and no __dict__ for setting new attributes
```

Consider using `NamedTuple` instead of `__slots__`.

## @property decorator

Understand: when you've marked something as property, it won't be stored in `__dict__`.
It makes sense since `@property` is calculated on demand.

## Attribute Lookup Resolution

When you access an attribute, this lookup chain happens:

1. Check `__dict__` of an instance;
2. Check `__dict__` of a class;
3. Go up inheritance chain, respecting `MRO`.

## isinstance VS type

`isinstance` is recursive, whereas `type` is not.
`issubclass` checks whether a class is a subclass of another class.

## MRO

Given a class `C`, one can examine `MRO` by `C.mro()` or `C.__mro__`.
`MRO` is build using C3 linearization algorithm.

Roughly speaking, `MRO` works in a DFS manner from left to right,
although the algorithm is more complex than this.

`MRO` plays an important role in Mixin Classes.

## Decorators for Classes

Obviously, you can decorate classes.
You should use `functools.wraps` when you decorate a class too.
The video lecture below contains great examples of `functools.wraps` usage.

## Dunder methods

When you access an attribute of an instance, you first invoke `__getattribute__`,
If an attribute has not been found in an object, a class, and all superclasses,
you invoke `__getattr__`.

There are also `__setattr__` and `__delattr__` - these method are more straightforward:
they are invoked when you set an attribute and delete an attribute respectively.

One might want to use `functools.total_ordering` to implement comparison for objects.

## Decorators as Classes

You can implement parameterized decorators as classes.

## Hashing

By default, hash is equal for two the same objects (`id`s are equal).

# Lecture 1 ends here

## Links

https://www.youtube.com/watch?v=SJ8z-TF07s4&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=6
