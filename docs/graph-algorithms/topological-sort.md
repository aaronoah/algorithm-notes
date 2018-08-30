# Topological Sort

A topological sort, a.k.a Topo-sort, is performed on DAG ([Directed Acyclic Graph](../graph-algorithms/overview.md)) to compute a **linear ordering** of all the vertices in graph. It satisfies the following condition: if a graph _G_ contains an edge (_u_, _v_), then the vertex _u_ must appear before the vertex _v_ in the sorted ordering.

Unlike the general discussions in [sorting](overview.md) section, Topo-sort tries to layout a graph structure into a flatten distribution of vertices. This method is widely adopted in the industry, e.g. a manufacturing process of specific products might have numerous small procedures combined together and to compute a topological ordering of such procedures are critical for pipelining the manufacturing process as to reduce time & money cost.

There are many algorithms that can achieve the goal, here a version of Kahn's algorithm is discussed.

## Kahn's Algorithm

The idea of this algorithm takes advantage of [BFS](../searching/graph-search.md) and using in-degree of nodes and it is the easiest method to understand.

1. Compute the in-degree for each of the nodes within the graph, initialize a count for _visited nodes_ to 0.

2. Enqueue all the nodes with in-degree of 0 to _queue_.

3. Dequeue a node from _queue_, increase the count for _visited nodes_ by 1, decrease the in-degree by 1 for all its neighboring nodes; If any of these nodes happen to have in-degree of 0, enqueue them to _queue_.

4. Repeat step 3 until _queue_ is empty.

5. If the count of _visited nodes_ is not equal to the number of nodes in the graph, then it is not [DAG](../graph-algorithms/overview.md) and topo-sort is impossible to complete.

Unlike traversing the solution using [DFS](../searching/graph-search.md) that revisit some of the nodes that share the same routes from the source to the destination, this algorithm takes &Omicron;(n) time to visit all nodes, which is more favorable and easier to design.