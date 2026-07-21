# Dynamic Programming

## Iterative Bottom-Up DP

You can optimize an interative bottom-up DP
by only using a constant number of rows of a DP matrix.

## Problem decomposition

Consider breaking down the original problem into subproblems by:

* prefixes - X\[:i\];
* suffixes - X\[i:\];
* substrings - X\[i:j\].
* submatrices.

For example, given two strings `s1` and `s2`,
`dp[i][j]` may represent a metric on the prefixes `s1[i:]` and `s2[j:]`.

Recall: substring is not the same as a subsequence.

# Greedy

## Overview

Greedy algorithms are concerned with tactics and not so much with strategy.
