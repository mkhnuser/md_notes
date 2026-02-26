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

Note that deletion operation deletes the first found node.
If you want to delete all the nodes, call this procedure multiple times.

## Balanced Binary Search Trees

A Binary Search Tree can become unbalanced.
Balanced Binary Search Trees are trees which cut the search space by 2 while searching.
The two main types of Balanced Binary Search Trees are AVL Trees and Red-Black Trees.

## AVL Trees

# TODO: Learn.

## Red-Black Trees

# TODO: Learn.

## Priority Queues

In some cases you want to associate an element of a queue with its weight;
based on its weight, you construct a max-heap or a min-heap,
which define what's known as a Priority Queue.
