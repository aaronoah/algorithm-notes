# Tree

When talking about [Tree](#tree) data structure, we normally omit the term _**free**_ that a _free tree_ is an acyclic, connected, undirected [graph](../graph-algorithms/overview.md). And a possibly disconnected acyclic undirected graph is _forest_.

Theorem. 1. A _G = (V, E)_ is an undirected graph, then

1. _G_ is a _free tree_.
2. any two vertices in _G_ are connected through a single path.
3. _G_ is connected, but removing an edge will result in a disconnected graph.
4. _G_ is connected, acyclic and |_E_| = |_V_| - 1.
5. if adding any single edge to |_E_| will cause the graph to form a cycle.

## Rooted Tree and Ordered Tree

A [Rooted Tree](#rooted-tree-and-ordered-tree) is a _free tree_ that has a virtual topmost node distinguishable from others which called the _root_ of the tree.

The children of a tree node is called the _descendant_ of that node and every children call their parent node the _ancestor_. Child nodes under the same node call each other _siblings_ and node with no children is called _leaf_ (external node), a non-leaf node is _internal node_.

The length of a path from _root_ of a tree to a node x is the _**depth**_ of x in the tree (the _**depth**_ of _root_ is 0). The _**height**_ of a node in a tree is the value of longest path leading from that node to a leaf in the tree; it generalizes to a formula for computing:

&hscr;(x) = max( &hscr;(_left subtree of x_), &hscr;(_right subtree of x_)) + 1

An [ordered tree](#rooted-tree-and-ordered-tree) is a rooted tree in which children of each node are ordered. e.g. a node in a tree has _k_ children, then it has 1<sup>th</sup>, 2<sup>nd</sup>, .. k<sup>th</sup> child.

_Note: most of the tree data structure we use is a **rooted tree** for analysis simplicity._

## Binary and _k_-ary Tree

A [Binary tree](#binary-and-k-ary-tree) is defined on a set of nodes that either contains no nodes or is composed with the _root_ node, its connected left subtree and a corresponding right subtree.

In a binary tree structure, filling all missing children of nodes with empty nodes of no descendants will result in a structure called _**full binary tree**_.

For trees that have more than 2 children per node, every node (includeing the _root_) in such a tree has no more than _k_ number of children. It is termed as a _k_-ary Tree.

A _**complete k-ary tree**_ is a tree in which all leaves have the same _depth_ and all non-leaf nodes have _k_ direct children.

## Table of Contents

* [AVL Tree](avl-tree.md) - a trivial implementation of a balanced binary tree.
* [Red-Black Tree](red-black-tree.md) - a prevalent balanced binary tree implementation.
* [Heap](heap.md) - a special tree structure facilitates various applications such as [priority queue](https://en.wikipedia.org/wiki/Priority_queue) and [heap sort](../sorting/heap-sort.md).
* [B-Tree](b-tree.md) - a disk based tree structure, particularly useful in database design.
* [Disjoint-Set](disjoint-set.md) - a set operation that finds relevance among data and build up forests for faster manipulations.
* [Threaded Binary Tree](threaded-binary-tree.md) - a special form of binary tree that connect leaves to parents, useful in designing Morris traversal, which require &Omicron;(1) extra space.
