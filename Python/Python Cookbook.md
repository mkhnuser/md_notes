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

### Chapter 4 - Iterators and Generators
