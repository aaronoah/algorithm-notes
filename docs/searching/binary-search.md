# Binary Search

[Binary Search](#binary-search) is built around the foundation of [Divide-and-Conquer](../divide-and-conquer/overview.md) and its fundamental idea is to locate an item in an ordered list of items in a recursive way.

It is worth noted that performing binary search operation in whatever structures of ordered items are the same given the premise traversing through the items is relatively costless. Whereas, performing INSERTION or DELETION operations in commonly seen sorted structures such as Array or List takes up to &Omicron;(n) complexity; While a prevalent implementation that involves a concept of [Tree](../tree/overview.md), [Binary Search Tree](#binary-search-tree) could boost the INSERTION and DELETION operations, meanwhile rapidly solve searching problems in a simple yet robust way.

_Note: If only demanding fast lookup operation in the algorithm design, the [Hash Table](hash-table.md) would be better given its &Omicron;(1) running time_.

## Pseudocode

```
BINARY_SEARCH(array, start, end, target)
  middle := (start + end) / 2
  if array[middle] = target
    return array[middle]
  else if array[middle] > target
    BINARY_SEARCH(array, start, middle - 1, target)
  else if array[middle] < target
    BINARY_SEARCH(array, middle + 1, end, target)
```

---

## Binary Search Tree (BST)

[BST][BST] is organized on the basis of a structure of binary tree and is a [_rooted tree_](../tree/overview.md); It could be represented in a dynamic list wherein the nodes contain information about pointer to the _left_, _right_ and _parent_ subtree.

<figure style="text-align:center">
  <img src="../images/binary_search_tree.png" />
  <figcaption>Figure 1. Binary Search Tree Graphical Representation</figcaption>
</figure>

The design idea of [BST][BST] is that given every possible node _x_ in the tree, all _keys_ in the left subtree are smaller than _x_ while all _keys_ in the right subtree are larger than _x_.

### Traversal of BST

Traverse through an entire structure of [BST][BST] recursively or iteratively has three distinct ways: **in-order tree walk**, **pre-order tree walk** and **post-order tree walk**.

* In-order Tree Walk

The output _key_ entries of sub-trees follows the pattern of _left_ subtree, _root_ and _right_ subtree. e.g. the In-order Tree Walk of Figure 1 binary tree yields _1, 3, 4, 6, 7, 8, 10, 13, 14_.

* Pre-order Tree Walk

The output _key_ entries of sub-trees follows the pattern of _root_, _left_ subtree and _right_ subtree. e.g. the Pre-order Tree Walk of Figure 1 binary tree yields _8, 3, 1, 6, 4, 7, 10, 14, 13_.

* Post-order Tree Walk

The output _key_ entries of sub-trees follows the pattern of _left_ subtree, _right_ subtree and _root_. e.g. the Post-order Tree Walk of Figure 1 binary tree yields _1, 4, 7, 6, 3, 13, 14, 10, 8_.

### Searching Performance

Basic operations cost of a [Binary Search Tree](#binary-search-tree) is proportional to the _height_ of such tree. Given a randomly built binary search tree with n _keys_, it is expected to have a tree of **height** log(n) and the searching consumption is &Theta;(log n).

It requires a [worst-case](../asymptotic-analysis.md) running time of &Omicron;(n) if the arriving sequence of data is monotonically increasing or decreasing during the binary tree formation. Additionally, during the INSERTION or DELETION operations on the tree, there is possibility that properties of [binary tree](../tree/overview.md) are violated. Therefore, it is necessary to form a tree structure with a relative **balanced** entry distribution called Balanced Binary Search Tree (BBST), which means both sides of the tree or subtree have a relative same **height**. In order to maintain such property of BBST even during massive INSERTION or DELETION operations on the tree, a special [Rotation](#rotation) operation comes into play.

### Rotation

Rotations are called when the BBST properties are violated. There are two kinds of rotations: _left rotation_ and _right rotation_; they both operate on the pointers among the nodes to maintain the _balanced_ features of the tree.

* Left Rotation

This method is called when (in [AVL Tree](../tree/avl-tree.md), height difference between the right subtree and the left subtree is more than 1).

As shown in figure 2, _left rotate_ operation can be formalized as LEFT-ROTATE(T, y), which transforms the right child of y to be the parent of y in the new tree and assigns the &beta; child of x to y.

<pre>
<code>
LEFT_ROTATE(T, y)
  x = y.right
  y.right = x.left
  if x.left &ne; null
    x.left.parent = y
  x.parent = y.parent
  if y.parent == null
    T.root = x
  else if y == y.parent.left
    y.parent.left = x
  else
    y.parent.right = x
  x.left = y
  y.parent = x
</code>
</pre>

* Right Rotation

This method is called when (in [AVL Tree](../tree/avl-tree.md), the height difference between the left subtree and the right subtree is more than 1).

As shown in figure 2, _right rotate_ operation can be formalized as RIGHT-ROTATE(T, x), which transforms the left child of x to be the parent of x in the new tree and assigns the &beta; child of y to x.

<pre>
<code>
RIGHT_ROTATE(T, x)
  y = x.left
  x.left = y.right
  if y.right &ne; null
    y.right.parent = x
  y.parent = x.parent
  if x.parent == null
    T.root = y
  else if x.parent.left = x
    x.parent.left = y
  else
    x.parent.right = y
  y.right = x
  x.parent = y
</code>
</pre>

<figure style="text-align:center">
  <img src="../images/binary_tree_rotation.gif" />
  <figcaption>Figure 2. Binary Search Tree Rotations</figcaption>
</figure>

---

### Prevalent Implementations of Balanced Search Tree

There are popular implementations like AVL Tree and Red-Black Tree in practice, and they both propose solutions to help search operation obtain a guaranteed &Theta;(log n) complexity.

* [AVL Tree](../tree/avl-tree.md) - a first balanced binary search tree structure ever invented.
* [Red Black Tree](../tree/red-black-tree.md) - a sophisticated while popular **balanced** search tree in various systems.
* [Splay Tree](http://www.cs.cornell.edu/courses/cs3110/2011sp/recitations/rec25-splay/splay.htm) - a self-adjusting structure to achieve a **balanced** search tree.
* [2-3 Tree](http://pages.cs.wisc.edu/~vernon/cs367/notes/10.23TREE.html) - a distinct tree structure designed to provide BBST solution with high performance for INSERTION operation.
* [B-Tree](../tree/b-tree.md) - a practical data structure designed for the database.

[BST]: #binary-search-tree-bst
