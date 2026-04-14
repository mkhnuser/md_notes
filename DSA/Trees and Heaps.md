# Trees

## n-ary trees

If a node has no more than n children, then we call such a tree an n-ary tree.
A General Tree -> A Binary Tree -> A Binary Search Tree.

## Binary Search Tree is an Online Data Structure

An advantage of using a tree over a binary search for searching
is that a tree is an online data structure, whereas a binary search is an offline one.

You can expand a tree as your program executes,
whereas you cannot (or, at least should not)
mutate an array during a binary search.

## Deletion in a Binary Search Tree

Suppose you want to delete a node `D` from a binary tree.

When you delete `D`, four cases are possible:

* 0 subtrees remain;
* 1 subtree remains;
* 2 subtrees remain;
* 3 subtrees remain.

And so you have to reconnect these subtrees.

### Two Simple Cases

1. `D` has no children;
2. `D` has precisely one child.

### One Complex Case

The complex case: `D` has two children.

You have to find a node which is:

1. Greater than all the nodes of the left subtree;
2. Less than all the nodes from the right subtree.

You can choose either the predecessor `P` of `D` or a successor `S` of `D`.
Suppose you chose `S`, and so now two cases are possible:

1. `S` is `D`'s immediate right child.
2. `S` is somewhere in the `D`'s right subtree.

## Balanced Binary Search Trees

A Binary Search Tree can become unbalanced.
Balanced Binary Search Trees are trees which cut the search space by 2 while searching.
The two main types of Balanced Binary Search Trees are AVL Trees and Red-Black Trees.

## AVL Trees

# TODO: Learn.

## Red-Black Trees

# TODO: Learn.

## Tries

# TODO: Learn.

## Priority Queues

In some cases you want to associate an element of a queue with its weight;
based on its weight, you construct a max-heap or a min-heap,
which define what's known as a Priority Queue.
