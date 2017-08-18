# Randomized Algorithms

This section concerns about the i<sup>th</sup> order statistic selection problem and many other significant yet practical randomized algorithms.

## Randomized Selection

A computation task described as follows: Find the i<sup>th</sup> smallest element (also termed as the [i<sup>th</sup> order statistic](https://en.wikipedia.org/wiki/Order_statistic)) in a randomly distributed array.

In a more general question that to locate a median within a randomly distributed array, the fundamental idea of [randomized selection](#randomized-selection) is also useful, contributing in [Quick Sort][quick-sort] partition method as well.

### Pseudocode

```
RANDOMIZED_SELECT(array, order_statistic)
  if length(array) = 1
    return array[1]
  choose a pivot uniformly from array at random
  find the index i of that pivot
  if i = order_statistic
    return pivot
  else if i > order_statistic
    return RANDOMIZED_SELECT(array[1..i], order_statistic)
  else if i < order_statistic
    return RANDOMIZED_SELECT(array[i+1..], order_statistic)
```

### Algorithm Analysis

The average running time of RANDOMIZED SELECTION is &Omicron;(n) for every possible input length n.

_**Proof**_:

Define a _phase j_ where the set of pivot choices lies between the size of _n &sdot; (3/4)<sup>j+1</sup>_ and _n &sdot; (3/4)<sup>j</sup>_ (in each iteration, choosing a _central_ element that has 1/4 elements smaller than it and 1/4 elements larger than it makes the next length at least 3/4 of the current length).

It takes 50-50 to choose a random splitter that has a 25-75 split and thus _E(X)_ = 1 + 1/2 &sdot; _E(X)_, _E(X)_ = 2, where _X_ is number of iterations before central element is found.

<figure style="text-align:center">
  <img src="../images/rselect.png" />
</figure>

Then, by [linearity of expectation](discrete-probability.md),

_E(&Tau;(n))_ = cn &Sum; (3/4)<sup>j</sup> &sdot; _E(X<sub>j</sub>)_; _E(&Tau;(n))_ &les; 2 cn &Sum; (3/4)<sup>j</sup> = 8 cn

Then, the average running time is &Omicron;(n), proof ends.

## Randomized Quick Sort

A [Quick Sort][quick-sort] algorithm aims to swiftly sort the un-ordered elements in the array. With a randomized pivot selection method (borrowed from the idea of [**randomized selection**](#randomized-selection)) introduced to the phase of choosing _pivot_ of _**partition method**_, [Quick Sort][quick-sort] will have an efficiency of &Omicron;(n &sdot; log n) in the expected running time.

[quick-sort]: ../sorting/quick-sort.md
