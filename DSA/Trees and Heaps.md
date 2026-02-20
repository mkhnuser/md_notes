# Trees

## Overview

If a node has no more than n children, then we call such a tree an n-ary tree.
A General Tree -> A Binary Tree -> A Binary Search Tree (BST).

## Analysis of a General Tree

There are two ways to traverse a general tree: pre-order, post-order.

In the case of a Binary Search Tree,
there is a third option: Left-Middle-Right traversal (in-order traversal)
or Right-Middle-Left traversal.

## A Binary Search Tree Analysis

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

## Balanced Binary Search Trees

Balanced Binary Search Trees are trees which cut the search space by 2 while searching.

## AVL Trees

AVL Tree is a self-balanced binary binary tree which helps
you construct a balanced binary search tree - it avoids "a linked list problem".

## Priority Queues

In some cases you want to associate an element of a queue with its weight.
Priority Queues are often implemented using Heaps.
