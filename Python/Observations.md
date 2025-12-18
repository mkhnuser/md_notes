# General Observations

## Check whether a string is a number

Use this code if you want to check whether a string is a number:

    str.isnumeric(token.lstrip("+-"))

Plus or minus sign do not count as numbers so the check will fail.

## Sorting

Sorting is always stable in Python.
Python uses PowerSort algorithm which is based on TimSort.

https://docs.python.org/3/howto/sorting.html#sortinghowto
