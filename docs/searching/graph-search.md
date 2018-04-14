# Graph Search

In a typical [Graph](../graph-algorithms/overview.md) data structure, searching for existence of specified _keys_ in that structure is called the [graph search](#graph-search) algorithm, or in other words, the _graph traversal algorithm_.

There are in general two kinds of such traversal algorithms with distinct operation strategies, [breadth-first search](#breadth-first-search) and [depth-first search](#depth-first search), all of which assure there is no possibility that a node is visited more than once. In other words, the vertices are dynamically categorized into visited and unvisited sets during the search.

## Breadth-First Search

Conceptually, BFS is an algorithm to traverse for specific paths or locate entries in search tree or graph structures (directed or undirected graph); It starts with a _source_ entry and visit its neighbors first before moving on to the next level neighbors, repeatedly until the _target_ entry is reached. BFS has a wide application scenarios: web crawling, social networking, network broadcasting etc.

Basically, BFS adopts a _queue_ (First-In-First-Out) structure to store the forefront visited vertices to assist traversal in the next level.

```
BREATH_FIRST_SEARCH(graph, source, target)

  initialize visited_set, queue
  visited_set.add(source)
  queue.add(source)

  while(!queue.is_empty())
    vertex = queue.remove()

    if(vertex == target)
      return vertex
    else
      visited_set.add(vertex)

      for unvisited_vertex of vertex
        if(unvisited_vertex == target)
          return vertex
        else
          visited_set.add(unvisited_vertex)
          queue.add(unvisited_vertex)

  return null
```

The BFS search produces a conceptual tree structure that could also facilitates the understandings of BFS search:

<figure style="text-align:center">
  <img src="../images/bfs1.png" />
  <figcaption>Figure 1. An example Map of Germany with some connections between cities</figcaption>
</figure>

<figure style="text-align:center">
  <img src="../images/bfs2.png" />
  <figcaption>Figure 2. A tree obtained after BFS search starting from city Frankfurt</figcaption>
</figure>

* Algorithm Analysis

Time complexity could be expressed as &Omicron;(|_V_ + _E_|), wherein _E_ could be in the range &Omicron;(1) ~ &Omicron;(|_V_|<sup>2</sup>), depending on how sparse the graph is. BFS in general is a memory-based algorithm thus if the graphs are too large to store in memory, it is more practical to interpret the complexity differently: given the distance _d_ (number of edge traversals) to search an entry starting from a node, BFS takes &Omicron;(_b_<sup>_d_</sup>), where _b_ is the _average_ branching factor.

## Bidirectional Search

Bidirectional Search aims to search for the _target_ starting forwards from the starting entry and backwards from the end entry simultaneously. It is an overall better searching strategy than other forms of graph searching.

The reason bidirectional search outperforms the uni-search in any forms is that the search tree grows exponentially with search distance increases, therefore two smaller trees have fewer edges going outwards for searching. Technically, when the two searches come across, the time complexity would be &Omicron;(2 * _b_<sup>_d/2_</sup>).

_Note: the bidirectional search is generally determined by other basic types of searches: BFS, [Best-first](https://en.wikipedia.org/wiki/Best-first_search) and [A*](http://theory.stanford.edu/~amitp/GameProgramming/AStarComparison.html)_.

## Depth-First Search

As the name suggests, DFS is searching on a basis of depth while BFS is searching on a basis of breadth. DFS is a searching primitive that is designed to find entries in a search tree or graph structures. Specifically, it starts searching from the source and go as far as possible to the end of a branch before [backtracking](#backtracking); Whenever there is match of target(s), DFS would end.

Though DFS does not require complex data structures to assist searching task, it is recursive in nature that could consumes great amount of stack space. In the context of WEB, it is more favored to use BFS than DFS in searching.

```
DEPTH_FIRST_SEARCH(graph, source, target)
  for(unvisited_vertices of source)
    if(unvisited_vertex_v == target)
      return target
    else
      mark unvisited_vertex_v as visited
      DEPTH_FIRST_SEARCH(graph, v, target)

  return null
```

* Algorithm Analysis

Same as BFS, the time complexity would be expressed as &Omicron;(|_V_ + _E_|). It consumes almost &Omicron;(|_V_|) of stack space in the [worst case](../asymptotic-analysis.md) to store all vertices of the graph. When the graph is too large to traverse for result, it is commonly to set depth limit for DFS to avoid overuse of memory or disk spaces.

## Backtracking

Backtracking is a technique to find all solutions to a specified computation problem, e.g. a classic problem as to find all arrangements of eight queens in a chess board that all of queens can not attack each other.

Recursive as it is, backtracking incrementally builds the candidate solution pieces to the final solution and abandon partial candidates (backtracking) along the way. In other words, the procedure can be seen as traversing in a _search tree structure_ with backtracking between two node levels time to time:

<figure style="text-align:center">
  <img src="../images/treesearch.gif" />
  <figcaption>Figure 3. An Example of Backtracking problem Search Tree</figcaption>
</figure>

In a possible recursion rule, the solution candidates will go from {Root, A}, {Root, A, C}, {Root, A, D}, {Root}, {Root, B}, {Root, B, E} to arrive at the final solution. Obviously, the backtracking approach would outperform the [brute-force search](https://en.wikipedia.org/wiki/Brute-force_search) method by memoizing partial solution to the final one.

## Additional References

1. Wikibooks Bidirectional Search: https://en.wikibooks.org/wiki/Artificial_Intelligence/Search/Heuristic_search/Bidirectional_Search
