# Modules and Import System

## Overview

Python's import system is extremely complex and extensible.

## Import * syntax

`from module import *` syntax imports everything from a module.
If a module defines `__all__` dunder, then only listed variables are imported.

## Default Packages and Namespace Packages

Default packages contain `__init__.py`, whereas namespace packages do not.

## Absolute and relative imports

A relative import contains `.` in it, whereas an absolute does not.
The advantage of a relative import is that if you've changed the package name,
you don't have to change your import statements.

## Package import

When you import a package, you interpret its `__init__.py` file.
One can implement a facade pattern using `__all__` dunder.

https://youtu.be/SuRVWRRjb_U?list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&t=1854
https://youtu.be/SuRVWRRjb_U?list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&t=2322

## import a.b

When you do, for example, this:

`from .boo import Bar`

You will be able to access `boo`:

`print(boo)`.

https://youtu.be/SuRVWRRjb_U?list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&t=2065

## __main__.py in a package - executable packages

You can run `python -m package_name` to execute first its `__init__.py`, and then `__main__.py`.

## -m switch

Note that when you do `python -m a.b.c`, you add your current directory to `sys.path`.
Because of this, absolute imports will work.
However, if you do, `python a/b/c.py`, you add only `c.py`'s current directory to `sys.path`.

https://stackoverflow.com/questions/7610001/what-is-the-purpose-of-the-m-switch

## sys.modules

`sys.modules` caches module imports you've made.

## Links

https://www.youtube.com/watch?v=SuRVWRRjb_U&list=PLlb7e2G7aSpTTNp7HBYzCBByaE1h54ruW&index=9
https://www.youtube.com/watch?v=0oTh1CXRaQ0
