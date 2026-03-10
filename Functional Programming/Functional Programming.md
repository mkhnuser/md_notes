# Functional Programming

## Overview

Functional paradigm tries to utilize declarative programming as much as possible.
OOP, on the other hand, relies on a procedural programming,
which is a subset of imperative paradigm as such.

## Side Effects

Side effects are any effects caused by a function except for accepting
a user input and returning an output. The absence of side effects makes
a formal verification of your program much easier.

## Pure Functions

A function is a pure function if and only if:

1. It has no side effects;
2. Its return values are identical for identical arguments.

Naturally, it's extremely easy to test pure functions.

## First Class and Higher Order Functions

Functions are oftentimes first-class citizens - they can be assigned to a variable.
Higher order functions are functions which accept or return other functions.
