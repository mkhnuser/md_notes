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
Adjacency matrix requires O(V ** 2) space and is rarely used because of this.

### Adjacency List

Adjacency List is another way to store a graph in memory and its more efficient in terms of memory.

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

## BFS

One might use this wave algorithm
to find the shortest path from a starting vertex
to another reachable vertex.

Understand: BFS doesn't take into account edge weights;
it only takes into account the number of edges from a starting vertex to a destination.
To calculate the shortest path based on edge weights, use Dijkstra's algorithm.

## Dijkstra's Algorithm

One might use this algorithm to construct a shortest path tree:
given a starting vertex s, this tree contains the shortest paths to all
other reachable vertices.

The restriction for a graph is that a graph does not contain edges
with negative weights. For negative weights and negative cycles, use Bellman-Ford algorithm.
