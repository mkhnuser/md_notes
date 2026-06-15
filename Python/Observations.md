# General Observations

## Check whether a string is a number

Use this code if you want to check whether a string is a number:

    str.isnumeric(token.lstrip("+-"))

Plus or minus sign do not count as numbers so the check will fail.

## .rstrip

.rstrip does not remove suffix. It removes character set:

    >>> "https%3A%2F%2Fgithub.com%2Ffoo.json".rstrip(".json")
    'https%3A%2F%2Fgithub.com%2Ff'
    >>> # pathlib to the rescue.
    >>> import pathlib
    >>> pathlib.Path("https%3A%2F%2Fgithub.com%2Ffoo.json").stem
    'https%3A%2F%2Fgithub.com%2Ffoo'

## Sorting

Sorting is always stable in Python.
Python uses PowerSort algorithm which is based on TimSort.

https://docs.python.org/3/howto/sorting.html#sortinghowto
