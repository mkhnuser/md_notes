# Dynamic Programming

## How does one approach dynamic programming problems?

One can oftentimes utilize recursion as the first step to solve dynamic programming problems.
Recursion can be further optimized using memoization: a top-down dynamic programming.
Memoization can be further improved with an iterative bottom-up dynamic programming.
From there, you can optimize your solution by only using a constant number of rows.

## Recursion + Memoization: a top-down approach

A top-down approach first considers the whole problem.
Then the whole problem is broken down into subproblems.
Memoization speeds up your solution and prevents the recursion stack from overflowing.

## Iteration: a bottom-up approach

A bottom-up approach solves small problems first.
After that, larger problems can be solved.
Eventually, an answer is obtained.

## Recursion vs a bottom-up approach

Conceptually:

* Recursion:

      A large step 1 ->
      a slightly smaller step 2 ->
      and even slightly smaller step 3 ->
      ... ->
      a base case.

* A bottom-up approach:

      a base case ->
      a trivial problem (of size 1, for example) ->
      a lightly bigger problem ->
      ... ->
      an answer to a large problem.

So, a bottom-up approach inverts recursion.

## Problem decomposition

Consider breaking down the original problem into subproblems by:

* prefixes - X\[:i\];
* suffixes - X\[i:\];
* substrings - X\[i:j\].

# Greedy

## Overview

Greedy algorithms are concerned with tactics and not so much with strategy.
