# Graphs

## Use Cases

* Game Development: tile is a vertex, and path is an edge;
* AI Decisions: state is a vertex, and path is a transition.

## Representation of Graphs in Memory

### Adjacency Matrix

One can use edge weights as a matrix values too for a weighted graph.
Adjacency matrix requires O(V ** 2) space and is rarely used because of this.

### Adjacency List

Adjacency List is another way to store a graph in memory.
It's more efficient than Adjacency Matrix in terms of memory.

### Edge List

Store edges in a list.

## Algorithms on Graphs

### DFS

To avoid cycles in DFS, you might color vertices: white, gray, black.
Both recursive and iterative implementations of DFS are possible.

### Topological Sorting on DAGs

One uses topological sorting for ordering tasks on DAGs.
One constructs the ordering above my examining leave times of nodes in the DFS procedure.

### Connected Components

One can use DFS to solve Counting The Number of Connected Components problem.

### BFS

BFS can be used to calculate shortest paths based on the number of edges.
When you implement BFS, you might find it useful to keep parents and distances arrays.

To calculate the shortest path based on edge weights,
use Dijkstra's algorithm.

#### Applications of BFS

* Web Crawling:

      You want to visit the content of the current page
      prior to visiting distant pages.

* Mazes.

### DFS and BFS on trees

Observe: you don't need any cycle-detection mechanism
such as coloring if a graph is a tree.

## Dijkstra's Algorithm

Dijkstra's algorithm applies to both directed and undirected graphs.
The restriction: no negative weights.

## Bellman-Ford Algorithm

# TODO: Learn.

## Minimum Spanning Trees (MST)

An MST of a graph is a spanning tree with the minimum weight.
For a minimum spanning tree to exist,
a graph is usually restricted to be connected.

## Prim's Algorithm

Uses a greedy approach and incrementally constructs MST.

## Kruskal's Algorithm

# TODO: Learn.
