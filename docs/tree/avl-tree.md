# Adelson-Velsky and Landis (AVL) Tree

[AVL Tree][avl-tree] is a type of [balanced binary search tree](../searching/binary-search.md) which is early invented data structure in binary search solutions. It requires a stable property that the absolute difference between the _height_ of the _left_ subtree of _root_ and the _height_ of the _right_ subtree of _root_ is no larger than 1.

## Height Guarantee

_Formal Claim_:

For every [AVL Tree][avl-tree] with &nscr; nodes, its _height_ &hscr; &les; 2 &sdot; log(n).

_**Proof**_:

define _N<sub>h</sub>_ is the minimum number of nodes in an AVL Tree of _height_ h, then

_N<sub>h</sub>_ = 1 + _N<sub>h-1</sub>_ + _N<sub>h-2</sub>_, _N<sub>h</sub>_ > 2 _N<sub>h-2</sub>_

Obviously, n = &Theta;(2<sup>h/2</sup>) (given that _N<sub>h</sub>_ = n, _N<sub>0</sub>_ = 1, _N<sub>1</sub>_ = 2), h < 2 &sdot; log(n)

_A more subtle claim_:

a [AVL Tree][avl-tree] has most height of 1.44 &sdot; log(n + 2).

_**Proof**_:

_N<sub>h</sub>_ has a lower bound &Omega;(k<sup>h</sup>), then

substituting _c &sdot; k<sup>h</sup>_ with both sides of the recurrence relation above yields:

c &sdot; k<sup>h</sup> &les; 1 + c &sdot; k<sup>h-1</sup> + c &sdot; k<sup>h-2</sup> = &Tau;(n)

in which to find out a _c, h<sub>0</sub>_ such that for every _h_ > _h<sub>0</sub>_, the inequality above holds.

Divided both sides by c &sdot; k<sup>h-2</sup>:

k<sup>2</sup> &les; k<sup>2-h</sup>/c + k + 1

wherein the term k<sup>2-h</sup> becomes relatively small when h grows very large, then the inequality will be satisfied if value of k is smaller than the solution to the equation: k<sup>2</sup> = k + 1, which is the [golden ratio](https://en.wikipedia.org/wiki/Golden_ratio) &phi; = 1.618... &ap; 1.62

Hence, n = &Omega;(&phi;<sup>h</sup>), conversely, h = &Omicron;(log<sub>&phi;</sub>n) &ap; 1.44 &sdot; log (n + 2)

## Performance Comparisons

comparing with [Red-Black Tree](red-black-tree.md), [AVL Tree][avl-tree] has a better lookup performance given its relative shorter _height_ of the tree: 1.44 &sdot; log(n + 2) < 2 &sdot; log(n + 1);

While the Red-Black Tree requires less costs during tree adjustments when INSERTION or DELETION operations happen than the AVL Tree does;

In conclusion, the AVL Tree is performant if used in scenarios where the number of element lookup dominates the number of element updates.

[avl-tree]: #avl-tree
