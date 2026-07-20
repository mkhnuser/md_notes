# Strings and Text

## Terminology

### Substring or subarray vs subsequence

Understand: substring or a subarray is contiguous, whereas a subsequence is not.
A relative order is always preserved in both cases.

Given: `s1 = "abcde"`, `s2 = "ace"`,
the longest common subsequence is `"ace"`, but `"ace"` is not a substring of `"abcde"`.

## Rope - Data Structure

Rope can be used to efficiently insert a substring into a string;
this data structure can be used be used to implement
a text editor insertion, for example.

## Prefix Functions

One can optimize prefix function calculation using a dynamic programming.
