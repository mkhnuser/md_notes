# Trees

## N-ary trees

If a node has no more than n children, then we call such a tree an n-ary tree.

* A General Tree;
* A Binary Tree;
* A Binary Search Tree.

## Onlineliness

An advantage of using a binary search tree over a binary search
is that a tree is an online data structure, whereas a binary search is an offline one.

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

## Tries

# TODO: Learn.

## AVL Trees

# TODO: Learn.

## Red-Black Trees

# TODO: Learn.

## Heaps & Priority Queues

### Heap Properties

The heap structure property:
heaps are to be populated from left to right so that they are complete.

The heap ordering property.

### Heap operations

* push an element to the heap:

      Add element to the end of the heap thus maintaining the heap structure,
      then sift this element up thus maining the heap ordering property.

* pop min / max:

      Prior to returning the top min / max element,
      place the last element at the root thus maining the heap structure,
      and then sift this element down thus maintaining the heap ordering property.

* heapify:

      Given an input array, construct a min / max heap efficiently.

* heap sort:

      Sort an array using heap operations.

Make sure you handle the case when a heap is empty or it has only one element.
Heap operations can be implemented both recursively and iteratively.

### Heap Use Cases

* Maintain a global minimum or a global maximum;
* K largest / k smallest elements;
* Task scheduling.
