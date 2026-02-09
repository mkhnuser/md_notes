# Trees

## Overview

Trees allow you to represent hierarchical structures: organization, taxonomy.
In trees, edges have a direction, trees are also acyclic.

## Nomenclature

The height of a tree is the longest path from the root to a leaf.
If a node has no more than n children, then we call such a tree an n-ary tree.
Note: not every binary search is a binary search tree.

## Analysis

The worst-case scenario for searching is O(n), where n is the number of nodes;
think of a linked list, for example.

An advantage of using a tree over a binary search for searching is that
a tree is an online data structure, whereas a binary search offline.
