# Red Black Tree

[Red Black Tree][red-black-tree] is a type of [balanced binary search tree][binary-search-tree]. It adds a bit to stand for the _color_: RED or BLACK, of each node.

_Formal Def_:

A [Red Black Tree][red-black-tree] is a type of [binary search tree][binary-search-tree] that follows the properties below:

1. Each node is either RED or BLACK
2. The _root_ is BLACK
3. All leaf nodes (NIL) are BLACK
4. If a node is RED, both of its children are BLACK
5. Every path from a node to its leaves contains the same number of BLACK nodes (_Def: the number of black nodes from a chosen node &xscr; to a NIL leaf (node &xscr; is not included) is called the **black-height**_ (bh(&xscr;)) of such node, the number of black nodes from **root** to any NIL leaves is the **black-height** of the total red-black tree)

## Height Guarantee

_Formal Claim_:

For every [red-black tree][red-black-tree] with &nscr; nodes, its height &hscr; &les; 2 &sdot; log<sub>2</sub> (n + 1).

_**Proof**_:

First, there are at least 2<sup>bh(x)</sup> - 1 number of internal nodes rooted from node x.

By simple induction, the base case: if height of tree x is 0, then there is 2<sup>0</sup> - 1 = 0; for tree with height more than 0 with both child nodes, there are at least 2<sup>bh(x) - 1</sup> - 1 internal nodes for each child node. Therefore, a rooted tree from x has at least 2 * (2<sup>bh(x) - 1</sup> - 1) + 1 = 2<sup>bh(x)</sup> - 1.

Presumably, for a given tree with height &hscr;, any paths leading from root to leaves have at least half of the nodes are black, in other words, the bh(_root_) &ges; &hscr;/2; then

_n_ &ges; 2<sup>&hscr;/2</sup> - 1, &hscr; &les; 2 log(n+1)

guarantee holds, proof ends.

[red-black-tree]: #red-black-tree
[binary-search-tree]: ../searching/binary-search.md
