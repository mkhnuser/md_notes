# Graphs

## Overview

Here are some examples of situations which can be modelled by graphs:

* Railroad network;
* Social network;
* Dependency graph;
* Planning graph.

## Representation of Graphs in Memory

### Adjacency Matrix

One can use edge weights as a matrix values too for a weighted graph.
Adjacency matrix requires O(V ** 2) space.

### Adjacency List

Adjacency List is another way to store a graph in memory.

## DFS

To avoid cycles in DFS, you color vertices: white, gray, black;
both recursive and iterative implementations are possible.

## Topological Sorting on DAGs

One uses topological sorting for ordering tasks if they can be ordered;
it builds a dependency graph: a -> b -> c, which should be read as:
a depends on b and b depends on c.

## Connected Components

One can use DFS with coloring
to solve counting the number of Connected Components problem.
