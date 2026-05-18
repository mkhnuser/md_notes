# Observations

## General

!!! Always use for loops for comprehensions:

        visited_matrix = [[False for _ in range(m)] for __ in range(n)]

Don't use multiplication syntax.
Multiplication is error-prone for mutable objects.

## Binary Trees

* A reverse in-order traversal can be used to find kth-largest element of a BST:

      https://www.algoexpert.io/questions/find-kth-largest-value-in-bst
