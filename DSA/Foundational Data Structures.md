# Data Structures

## Overview

A data structure is a way of organizing information in computer memory.

## Linked List (Data Structure)

There is no `O(n)` reallocation routine which happens in dynamic arrays
upon insertion and deletion.

### Linked List Applications

* LRU Cache;
* Collision Resolution in Hash Tables.

## Stack (LIFO Abstract Data Type)

A stack might be based on a dynamic array or a linked list.

## Queue (FIFO Abstract Data Type)

A queue might be based on a circular buffer or a linked list.
A circular buffer implementation has a disadvantage of having fixed size.
If you don't want to have a fixed size, use a linked list as an underlying implementation.

## Deque (Abstract Data Type)

A Deque is a generalization of a stack and a queue.
A Deque allows you to push and pop from both sides of a deque.
A Deque can be implemented using a circular buffer with two pointers or using a doubly linked list with two pointers.
