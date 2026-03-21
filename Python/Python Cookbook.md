# Python Cookbook by David Beazley

## Overview

Below I note my personal favorite things from the book.

## Chapter 1 - Data Structures and Algorithms

### Recipe 1.10

Deduplicates elements of an iterable while preserving the order.

### Recipe 1.18

Use `._replace` method to create a brand-new named tuple with updated fields.

### Recipe 1.19

Just a quick reminder: `sum((x ** 2 for x in s))` is the same as `sum(x ** 2 for x in s)` if
an outer function accepts only one argument.

### Recipe 1.20

`collections.ChainMap` can be used to chain two dictionaries together;
references to original dictionaries is kept - no new dics are created.

### Chapter 1 Conclusion

The chapter contains a lot of info on dictionary manipulations & min / max & sorting.

## Chapter 2 - Strings and Text

### Recipe 2.14

Recall: `"a" "b"` results in concatenation of the two strings.
The behavior above can be especially tricky while working with sequences.

This recipe also contains a discussion on efficient text streaming
using generators and batching.

### Chapter 2 Conclusion

The chapter contains a lot of information on regular expressions
and text manipulation, HTML & XML including. This chapter also addresses
text tokenization, which is used in programming languages construction.

## Chapter 3 - Numbers, Dates, and Times

### Recipe 3.2

Perhaps, you should use `decimal` module only for the domain of finance
since `decimal` introduces a lot of overhead over plain `float` type.

A mind-blowing piece of code:

    nums = [1.23e+18, 1, -1.23e+18]
    sum(nums)
    0.0

### Chapter 3 Conclusion

The chapter discusses various discussions on
number precision, formatting, and representation.
It also contains useful information on `datetime` module.

## Chapter 4 - Iterators and Generators

### Recipe 4.5

Iterate a file in reverse.

### Recipe 4.15

Great usage of `heap.merge` function.

### Chapter 4 Conclusion

The chapter discusses `zip`, `reversed`, advanced iteration, and `itertools` module.
When faced with a complex iteration pattern, consult `itertools` documentation.

## Chapter 5 - Files and I/O

### Recipe 5.4

Discusses a gotcha when dealing with byte strings.

### Recipe 5.5

Discusses `io.StringIO` and `io.BytesIO`: these objects allow you to obtain a file-like
interface to a string.

### Recipe 5.8

Discusses how to iterate a file in chunks.

### Recipe 5.9

Discusses `memoryview` function.

### Recipe 5.10

Discusses `mmap` module and briefly discusses memory mapping concept as such.

### Recipe 5.21

A great example of usage of `pickle` module for Python object serialization,
which can later be stored in a DB, transferred over a network, or written to a file.

### Chapter 5 Conclusion

The chapter explains that bad file names or bad encoding can crush your program;
it also explains that an interaction with a file system in Python is built in layers,
and so you can hack it by accessing lower levels.

## Chapter 6 - Data Encoding and Processing

### Chapter 6 Overview

The chapter teaches you to work with JSON, XML, and DB Drivers.

## Chapter 7 - Function

### Recipe 7.5

A perfect usage of a sentinel `object()` pattern as the default parameter.
There is a distinction between passing no value and passing a value of `None`,
just like in many publisher-subscriber patterns, for example.

The recipe also explains that any default arguments are calculated at
a function definition time.

### Recipe 7.7

The recipe demonstrates how to capture variables while using `lambda` functions.

### Recipe 7.8

Greatly demonstrates the usage of `functools.partial`.

### Chapter 7 Overview

The chapter, toward the end, examines advanced usage of callback functions.
