# Topological Sort

A topological sort, a.k.a Topo-sort, is performed on DAG ([Directed Acyclic Graph](../graph-algorithms/overview.md)) to compute a **linear ordering** of all the vertices in graph. It satisfies the following condition: if a graph _G_ contains an edge (_u_, _v_), then the vertex _u_ must appear before the vertex _v_ in the sorted ordering.

Unlike the general discussions in [sorting](overview.md) section, Topo-sort tries to layout a graph structure into a flatten distribution of vertices. This method is widely adopted in the industry, e.g. a manufacturing process of specific products might have numerous small procedures combined together and to compute a topological ordering of such procedures are critical for pipelining the manufacturing process as to reduce time & money cost.

There are many algorithms that can achieve the goal, here a version of Kahn's algorithm and [BFS](../searching/graph-search.md) are discussed.

## Kahn's Algorithm



## BFS approach

