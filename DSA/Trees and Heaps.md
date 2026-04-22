# Trees

## N-ary trees

If a node has no more than n children, then we call such a tree an n-ary tree.

* A General Tree;
* A Binary Tree;
* A Binary Search Tree.

## Onlineliness

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

## AVL Trees

# TODO: Learn.

## Red-Black Trees

# TODO: Learn.

## Tries

# TODO: Learn.

## Priority Queue

One sometimes wants to associate a node with a weight.
In this case, you get a priority queue: efficiently obtain a max element or a min element.

Priority Queue is usually built on a Heap Data Structure;
there are many types of heaps.
