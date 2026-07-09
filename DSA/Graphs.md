# Graphs

## Representation of Graphs in Memory

### Adjacency Matrix

One can use edge weights as a matrix values too for a weighted graph.
Adjacency matrix requires O(V ** 2) space and is rarely used because of this.

### Adjacency List

Adjacency List is another way to store a graph in memory.
It's more efficient than Adjacency Matrix in terms of memory.

### Edge List

Store edges as a list of lists.

## Applications of Graph Algorithms

### Topological Sorting on DAGs

One uses topological sorting for ordering tasks given a DAG.

The topological sorting ensures that for every edge a -> b,
in topological ordering a comes before b.

### Connected Components

One can use DFS with coloring to calculate the number of connected components.

### Graph Level-order traversal

You might use BFS for level-order traversal:
examine all the elements which currently can be found in a queue.

## Dijkstra's Algorithm

Dijkstra's algorithm applies to both directed and undirected graphs.

The restriction on graphs: no negative weights, and hence no negative weights cycles.
To overcome this restriction, use Bellman-Ford.

## Bellman-Ford Algorithm

# TODO: Learn.

## Prim's Algorithm

Prim's operates on a weighted undirected graph.
Therefore, any starting vertex can be chosen.

## Kruskal's Algorithm

# TODO: Learn.
