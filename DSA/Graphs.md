# Graphs

## Overview

Here are some examples of situations which can be modelled by graphs:

* Railroad network;
* Social network;
* Dependency graph.

## Representation of Graphs in Memory

### Adjacency Matrix

One can use edge weights as a matrix values too for a weighted graph.
Adjacency matrix requires O(V ** 2) space and is rarely used because of this.

### Adjacency List

Adjacency List is another way to store a graph in memory and its more efficient in terms of memory consumption.

## Algorithms on Graphs

### DFS

To avoid cycles in DFS, you color vertices: white, gray, black;
both recursive and iterative implementations of DFS are possible.

### Topological Sorting on DAGs

One uses topological sorting for ordering tasks if they can be ordered;
topological sorting builds a dependency graph: a -> b -> c, which should be read as:
a depends on b & b depends on c.

One constructs the ordering above my examining leave times of nodes in DFS procedure.

### Connected Components

One can use DFS to solve Counting The Number of Connected Components problem.

### BFS

One might use this wave algorithm to find the shortest path from a starting vertex
to another reachable vertex. Edge weights are not taken into account, but rather the
number of edges are taken into account.

To calculate the shortest path based on edge weights, use Dijkstra's algorithm.

### Dijkstra's Algorithm

One uses Dijkstra's Algorithm to construct a shortest path tree:
given a starting vertex s, this tree contains the shortest paths to all
other reachable vertices from s.

The restriction for a graph is that a graph does not contain edges
with negative weights;
for negative weights and negative weight cycles, use Bellman-Ford algorithm.

## Bellman-Ford Algorithm

# TODO: Learn.

## Minimum Spanning Trees (MST)

An MST of a graph is a spanning tree with the minimum weight.
Two main algorithms for MST finding are:

### Prim's Algorithm

This algorithm examines a graph on a per-node basis and keep track of a MST.

### Kruskal's Algorithm

# TODO: Learn.
