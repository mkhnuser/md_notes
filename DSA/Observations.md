# Observations

## Overview

This note contains observations and useful problems.

## Binary Trees

* A reverse in-order traversal can be used to find kth-largest element of a BST:

      https://www.algoexpert.io/questions/find-kth-largest-value-in-bst

## Graphs

* DFS Cycle Detection:

      DFS cycle detection for directed graphs is different from undirected ones.
      Keep the parent reference in an undirected graph case.

      https://neetcode.io/problems/valid-tree/question

* Prim's vs Kruskal's:

      The main advantage of Kruskal's over Prim's
      is that one can control inclusion / exclusion of edges:

      * Introduce an edge into a minimum spanning tree (force an edge to be present);
      * Exclude an edge from a minimum spanning tree.

      https://neetcode.io/problems/find-critical-and-pseudo-critical-edges-in-minimum-spanning-tree/question.

## Heaps and Priority Queues

* Neetcode contains iterative heap implementations:

      https://neetcode.io/courses/dsa-for-beginners/25

## Dynamic Programming

* To optimize a bottom-up solution, consider the usage of only two rows at a time.

## Investigate further:

* Floyd's Tortoise and Hoare Algorithm;
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
      https://neetcode.io/problems/delete-leaves-with-a-given-value/question

* Investigate RMQ and LCA problems.
* Prefix Sums:

      https://neetcode.io/problems/range-sum-query-2d-immutable/question

* Iterative backtracking:

      Investigate how iteration can be used to solve backtracking problems.

* Frequency count:

      https://neetcode.io/problems/reorganize-string/question
