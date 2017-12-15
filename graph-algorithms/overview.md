# Graph Algorithms

[Graph Theory](https://en.wikipedia.org/wiki/Graph_theory) is a study of _graphs_, a mathematical structure modeling the associations between objects. It is vital for many computer science problems and worth attention for not only theoretical studies but also practical application development.

This chapter discusses fundamental graph structures, typical graph problems and correlated algorithm analysis. Specifically, graph searching primitives such as DFS and BFS are the most important techniques throughout the graph algorithms.

## Graph Definitions

Generally, there are two kinds of graphs: [directed graph](#directed-graph) and [undirected graph](#undirected-graph). Both of them involve a relationship between **Vertex** _V_ and **Edge** _E_.

### Directed Graph

Given a graph _G_ = (_V_, _E_), wherein the _V_ is a set of vertices of _G_ and _E_ is a set of edges going in and out from vertices with directions, connected them together. Specifically, given vertices {1, 2, 3, 4, 5, 6}, a graph can be built like below:

<figure style="text-align:center">
  <img src="../images/directed-graph.png" />
  <figcaption>Figure 1. Directed Graph</figcaption>
</figure>

_Note: there are cycles (even self cycles, a vertex points to itself) in directed graphs and to be noted that problems like [topological sort](../sorting/topological-sort.md) could not have solutions if cycles present, the directed graph with no cycles is called DAG (directed acyclic graph)_.

### Undirected Graph

Unlike [directed graph](#directed-graph), undirected graph only has edges with no directions between connected vertices. Since the relations among vertices have no ordering, there exists no self cycles. Similarly,

<figure style="text-align:center">
  <img src="../images/undirected-graph.png" />
  <figcaption>Figure 2. Undirected Graph</figcaption>
</figure>

### Degrees

In an [undirected graph](#undirected-graph), the degree of a vertex means the number of edges associated with that vertex. For instance, the degree of vertex 3 in the above graph is 3;

While in the [directed graph](#directed-graph), the degree of a vertex is the summation of its **in-degree** and **out-degree**. Such **in-degree** means the number of edges pointing towards the vertex and **out-degree** means the number of edges pointing out of the vertex.

_Note: the vertex with zero degree means it is a lonely island, disconnected from any other vertices in the graph_.

### Connectivity

If for any given vertices in an [undirected graph](#undirected-graph), there exists paths reachable from all other vertices, then the graph is _connected_. Specifically, if an undirected graph _G_ = (_V_, _E_) is connected, the number of edges is larger than or equal to number of vertices minus 1: |_E_| &ge; |_V_| - 1.

There are only definitions of **strongly connected** and **weakly connected** in a [directed graph](#directed-graph). In a **strongly connected** directed graph _G_ = (_V_, _E_), for any two distinct vertices x, y within _V_, there exists paths from x to y and from y to x;

Substituting all directional edges of a directed graph with undirected ones could obtain a _base graph_ of the original graph. If such a _base graph_ is **connected**, then the original directed graph is **weakly connected**.

## Graph Representations

Two vertices sharing a same edge are _adjacent_ in a graph. To define such relationships among vertices, two practical uses of data structures are introduced: [adjacency matrix](#adjacency-matrix) and [adjacency list](#adjacency-list).

### Adjacency Matrix

This matrix (e.g. _adj[][]_) is a 2D array with size |V| &cross; |V|; In an undirected graph, if vertex _a_ and vertex _b_ are connected, then adj[a][b] = 1 and adj[b][a] = 1; if there are no edges between say vertex _e_ and vertex _c_, then adj[e][c] = 0, adj[c][e] = 0;

For a directed graph, the matrix cell value depends on the existance of directional edges; If vertex _a_ has an edge going outward to vertex _b_ while vertex _b_ has no edges going inward to vertex _a_, then adj[a][b] = 1 but adj[b][a] = 0

<figure style="text-align:center">
  <img src="../images/adjacency-matrix.jpg" />
  <figcaption>Figure 3. Adjacency Matrices of a Directed Graph and an Undirected Graph</figcaption>
</figure>

Adjacency matrix is practical when the graph is **dense** (at least one edge going in between two vertices) and finding the existence of edges is immediate (LOOKUP costs &Omicron;(1)). It is less so if the graph is sparse (the graph topology structure approaches a _**forest**_ rather than a graph).

### Adjacency List

Adjacency list is an array of linkedlist in design and it costs only &Omicron;(|V| + |E|) compared to [adjacency matrix](#adjacency-matrix). In addition, the array can be dynamic which means adding vertices to a graph is easier than a static structure like adjacency matrix.

<figure style="text-align:center">
  <img src="../images/adjacency-list.png" />
  </figcaption>Figure 4. Adjacency List of a Directed Graph</figcaption>
</figure>

Though it normally costs &Omicron;(|E|) time to LOOKUP edge associations, it is a preferable choice than adjacency matrix in a massive-scale data network such as WEB.

## Table of Contents

* [Breadth-First Search](../searching/graph-search.md) - a searching primitive prototype for many important algorithms like [Minimum Spanning Tree] and [Dijkstra Shortest Path].
* [Depth-First Search](../searching/graph-search.md) - in contrast to BFS, DFS provides a simple recursive implementation.
* [Shortest Path Algorithms](shortest-path.md) - a prevalent type of graph algorithm in practice, e.g. find a shortest path from location A to location B in map.
* [Minimum Spanning Tree](minimum-spanning-tree.md) - a technique to transform graphs to trees
* [Graph Minimum-Cut](minimum-cut.md) - split the graph into different groups for applications like [community finding](https://en.wikipedia.org/wiki/Community_structure#Algorithms_for_finding_communities).
* [Topological Sort](topological-sort.md) - sort a [DAG](#directed-graph) graph with respect to its topological relations.
