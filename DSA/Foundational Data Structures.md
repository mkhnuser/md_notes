# Data Structures

## Overview

A data structure is a way of organizing information in computer memory.
A data structure defines operations which can be performed on data.
Careful choice of a data structure guarantees a more efficient performance.

## Linked List (Data Structure)

A linked list allows you to avoid insertion and deletion disadvantages of a dynamic array.
There will be no `O(n)` reallocation procedure which might happen in an array.
You sacrifice instantaneous element access which pertains to arrays.

### A Doubly Linked List (Data Structure)

Just as a linked list but has more edge cases.

### Interesting Linked List Applications

* LRU Cache;
* Collision Resolution in Hash Tables.

## Stack (LIFO ADT)

A stack might be based on a dynamic array or a linked list.

## Queue (FIFO ADT)

Provides interfaces, but might have many different internal implementations.
Each internal implementation has its advantages and disadvantages.

For example, a circular buffer implementation has a disadvantage of having fixed size.
If you don't want to have a fixed size, use a linked list as an underlying implementation.

## Deque (ADT which generalizes Stack and Queue)

A Deque allows you to push and pop from both sides of a deque.
A Deque can be implemented using a circular buffer with two pointers or using a doubly linked list with two pointers.
