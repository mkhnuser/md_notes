# Functional Programming

## Overview

Functional paradigm tries to utilize declarative programming as much as possible.
OOP, on the other hand, relies on a procedural programming,
which is a subset of imperative paradigm as such.

## Side Effects

Side effects are any effects caused by a function except for accepting
a user input and returning an output. The absence of side effects makes
a formal verification of your program much easier.

### I/O

Understand: I/O is a side effect too and should be avoided as much as possible.

## Pure Functions

A function is a pure function if and only if:

1. It has no side effects;
2. Its return values are identical for identical arguments.

Naturally, it's easy to read, test, and write pure functions.

## First Class and Higher Order Functions

Functions are oftentimes first-class citizens - they can be assigned to a variable.
Higher order functions are functions which accept or return other functions.

## Referential Transparency

A function invocation can be replaced with its value.
If a function is not referentially transparent, we call it referentially opaque.

https://www.baeldung.com/cs/referential-transparency#referential-transparency

## Memoization

Pure functions can be safely memoized.

## Parallelization

Pure functions can be easily parallelized.

## Recursion

Often, a recursive step can be split into:

1. Pre-recursive action;
2. Actual Recursion;
3. Post-recursive action.

## Closures

Closure refers to an ability of a function to access its enclosing scope.
In Python, beware of `nonlocal` and `global`, you don't need these keywords
to mutate mutable types: lists, dicts, etc.

## Currying

Currying is the process of transforming a function which takes multiple arguments
into a series of functions which accept only one.
