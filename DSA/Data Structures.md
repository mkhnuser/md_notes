# Data Structures

## Data Structures

A data structure is a way of organizing information in memory.
A data structure defines operations which can be performed on data.

## Linked List

A linked list allows you to avoid insertion and deletion disadvantages of a dynamic array.
There will be no `O(n)` reallocation procedure which might happen in an array.
You sacrifice instantaneous access which pertains to arrays.

## Stack (LIFO)

A stack might be based on a dynamic array or a linked list.

Some examples of where a stack might be used:

* Web Browser "go back" functionality;
* Text Editor Undo functionality (**).

** Proper undoing and redoing should act as a tree, but not as a stack.

## Queue (FIFO)

Provides interfaces, but might have many different internal implementations.
Each internal implementation has its advantages and disadvantages.
For example, a circular buffer implementation has a disadvantage of having fixed size.
If you don't want to have a fixed size, use a linked list.
