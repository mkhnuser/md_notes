# Data Structures

## Data Structures

A data structure is a way of organizing information in memory.
A data structure defines operations which can be performed on data.

## Linked List

A FIFO structure.

A linked list allows you to perform insertion and deletion efficiently, without `O(n)` time.
You sacrifice instantaneous look up.
A .length property might be implemented to obtain a length
of a linked list in `O(1)`.

## Stack

A LIFO structure.

Some examples:

* Browser "go back" functionality;
* Text Editor Undo functionality (**).

** - Actually, proper undoing and redoing should act as a tree, but not as a stack. Can you see why?

A stack might be based on a dynamic array or a linked list.

## Queue

A FIFO structure.

Provides interfaces, but might have many different internal implementations.
Each internal implementation has its advantages and disadvantages.
For example, a circular buffer implementation has a disadvantage of having fixed size.

If you don't want to have a fixed size, use a linked list.
