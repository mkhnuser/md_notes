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

## Topological Sorting on DAGs

One uses topological sorting for ordering tasks given a DAG.
The DAG does not have to be connected; there might be more than one component,
and, therefore, there might be more than one correct ordering.

The topological sorting ensures that for every edge a -> b,
in topological ordering a comes before b.

## Dijkstra's Algorithm

Dijkstra's algorithm applies to both directed and undirected graphs.

The restriction on graphs: no negative weights, and hence no negative weights cycles.
To overcome this restriction, use Bellman-Ford.

## Bellman-Ford Algorithm

# TODO: Learn.

## Prim's Algorithm

Prim's operates on a weighted undirected graph.
Choose any starting vertex and greedily build a tree.

## Kruskal's Algorithm

Kruskal's operates on a weighted undirected graph.
Sort edges and then utilize DSU.
