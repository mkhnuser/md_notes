# Observations

## Overview

This note contains observations and useful problems.

## General

!!! Always use for loops for comprehensions:

        visited_matrix = [[False for _ in range(m)] for __ in range(n)]

Don't use multiplication syntax.
Multiplication is error-prone for mutable objects.

## Binary Trees

* A reverse in-order traversal can be used to find kth-largest element of a BST:

      https://www.algoexpert.io/questions/find-kth-largest-value-in-bst

* You can cleverly serialize a binary tree (pattern matching / string):

      https://neetcode.io/problems/subtree-of-a-binary-tree/solution

* Lowest Common Ancestor (LCA):

      One can try to find LCA in a general tree or in a binary search tree.

      https://neetcode.io/problems/lowest-common-ancestor-in-binary-search-tree/question?list=neetcode150

## Heaps and Priority Queues

Neetcode contains iterative heap implementations:

      https://neetcode.io/courses/dsa-for-beginners/25
