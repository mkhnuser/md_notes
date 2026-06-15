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

## Investigate further:

* Floyd's Tortoise and Hoare Algorithm;
* Sliding window;
* Morris Traversal:

      https://neetcode.io/problems/kth-smallest-integer-in-bst/solution
      https://neetcode.io/problems/binary-tree-inorder-traversal/solution
      https://neetcode.io/problems/binary-tree-preorder-traversal/solution
      https://neetcode.io/problems/binary-tree-postorder-traversal/solution
      https://neetcode.io/problems/binary-tree-from-preorder-and-inorder-traversal/solution

* Quick Select:

      Quick Select is similar to the quick sort algorithm.

      https://neetcode.io/problems/k-closest-points-to-origin/solution
      https://neetcode.io/problems/kth-largest-element-in-an-array/solution


* A postorder traversal can be seen as a slight modification of a preorder one:

      https://neetcode.io/problems/binary-tree-postorder-traversal/solution
