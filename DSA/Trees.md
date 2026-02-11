# Trees

## Overview

Trees allow you to represent hierarchical structures: organization, taxonomy.
In trees, edges have a direction, trees are also acyclic.

## Nomenclature

The height of a tree is the longest path from the root to a leaf.
If a node has no more than n children, then we call such a tree an n-ary tree.

A General Tree -> A Binary Tree -> A Binary Search Tree (BST).

## Analysis of a General Tree

There are two ways to traverse a general tree: pre-print and post-print.
In the case of a Binary Search Tree,
there is a third option: Left-Middle-Right traversal or Right-Middle-Left traversal.

## Analysis of A Binary Search Tree

A Binary Search Tree usually preserves the following invariant:
given a node, all nodes in the left subtree are less than or equal to the node,
whereas all nodes in the right subtree are strictly greater than the node.

Because of the invariant above, you can quickly search in a binary tree.

An advantage of using a tree over a binary search for searching is that
a tree is an online data structure, whereas a binary search is offline.
That is, you can expand a tree as your program executes,
whereas you cannot (or, at least should not)
mutate an array when a binary search is running.

Insertion and Deletion from a BST should always preserve a BST invariant.

When you delete a node in a BST, you might obtain 0, 1, 2, or 3 trees.
Therefore, you should consider each of this cases separately.

Note that deletion operation deletes the first found node.
If you want to delete all the nodes, call this procedure multiple times.
