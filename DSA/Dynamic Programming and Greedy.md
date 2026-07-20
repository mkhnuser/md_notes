# Dynamic Programming

## How does one approach dynamic programming problems?

One can oftentimes utilize recursion as the first step to solve dynamic programming problems.
Recursion can be further optimized using memoization: a top-down dynamic programming.
Memoization can be further improved with an iterative bottom-up dynamic programming.

## Recursion + Memoization: a top-down approach

Memoization speeds up your solution and prevents the recursion stack from overflowing.

## Iteration: a bottom-up approach

Instead of relying on recursive descent,
an iterative bottom-up approach starts from the recursive base case.
Then, starting from the base, you solve trivial problems, and then you use solutions to
these trivial problems to solve larger problems and so on until you obtain an answer.

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

# Greedy

## Overview

Greedy algorithms are concerned with tactics and not so much with strategy.
