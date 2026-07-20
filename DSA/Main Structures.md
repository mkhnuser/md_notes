# Main Structures

## Overview

A data structure is a way of organizing information in computer memory.
Whereas, an abstract data type defines an interface to a data structures.

## Stack (Abstract Data Type)

A stack might be based on a dynamic array or a linked list.
It's a LIFO ADT.

## Queue (Abstract Data Type)

A queue might be based on a circular buffer or a linked list.
It's a FIFO ADT.

A circular buffer implementation has a disadvantage of having fixed size.
If you don't want to have a fixed size, use a linked list as an underlying implementation.

## Deque (Abstract Data Type)

A deque is a generalization of a stack and a queue.
It's both LIFO ADT and FIFO ADT.

A deque allows you to push and pop from both sides of a deque.
A deque can be implemented using a circular buffer with two pointers or using a doubly linked list with two pointers.

## Disjoint Set Union

Disjoint Set Union allows you to union disjoint elements and find their representatives.
