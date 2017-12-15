# Sorting

Many of programs we see today have something to do with sorting, that given an unsorted, randomly distributed array or list, research the best approach to sort in accordance to a specified alphabetical or numerical order.

## Terminologies

Key concepts are introduced in this chapter such as [Stable Sort](#stable-sort).

### Total Order

[Total Order](https://en.wikipedia.org/wiki/Total_order) is a binary relation on a set of elements that satisfies:

* Antisymmetry: if a &ges; b and b &ges; a, then a = b
* Transitivity: if a &les; b and b &les; c, then a &les; c
* Totality: either a &les; b or b &les; a or both

### Adaptive Sort

A sorting algorithm is an adaptive sort scheme if it takes advantage of existing order of an original inputs. The presortedness of the input sequence benefits the sorting algorithm to achieve better running time.

### Comparison-based Sort

Sorting algorithms that sort a list of elements base _only_ on the _comparisons of pairs_ without knowing other aspects of elements is **comparison-based sort**.

_Note: [Comparison-based Sort](#comparison-based-sort) assumes no preliminary knowledge about input arrays and thus the "general-purpose sorting method"; if not, some [non-comparison based sort](non-comparison-sort.md) could be highly useful._

#### Sorting Lower Bound

Formal Def: every [comparison-based sorting](#comparison-based-sort) has the [worst-case](../asymptotic-analysis.md) running time of &Omega;(n &sdot; log n).

_**Proof**_: given a randomly distributed array of length n, assume the maximal compares required to sort the entire array is k and there is _at least_ n! permutations to sort (each permutation is possible to yield the correct outcome); In each comparison, we obtain either a **True** or **False** that the element is displaced in the right location, then:

2<sup>k</sup> &ges; n!, by [pigeonhole principle](https://en.wikipedia.org/wiki/Pigeonhole_principle), 2<sup>k</sup> &ges; (n/2)<sup>n/2</sup>, k &ges; (n/2) &sdot; log (n/2)

According to [asymptotic analysis](../asymptotic-analysis.md), noting that k &ges; cn &sdot; log (cn), &Tau;(n) = &Omega;(n &sdot; log n)

### In-place Sort

Sorting scheme that only a constant number of elements or memory spaces are required to store outside the original array is In-place Sort.

In-place Sort only requires &Omicron;(1) extra space to sort the array. It usually sorts on the original array thus an useful approach to minimize the memory usage while sorting.

### Stable Sort

Stable sorting algorithm maintains the relative order of elements with same value. Mathematically, given two records &Rscr; and &Qscr; with same value, &Rscr; precedes &Qscr; in the original array, then a [Stable Sort](#stable-sort) will produce a sorted array with &Rscr; comes before &Qscr;.

## Table of Contents

* [Selection Sort](selection-sort.md) - a naive swapping-based sorting algorithm.
* [Bubble Sort](bubble-sort.md) - an improved swapping-based sorting technique.
* [Insertion Sort][insertion-sort] - mostly used approach in common sorting tasks.
* [Shell Sort](shell-sort.md) - a compensating algorithm for [worst-case](../asymptotic-analysis.md) [insertion sort][insertion-sort].
* [Heap Sort](heap-sort.md) - a type of sorting technique based on [min-heap](../tree/heap.md) or [max-heap](../tree/heap.md) data structures.
* [Merge Sort](merge-sort.md) - a typical [DnC][DnC] strategy in sorting tasks.
* [Quick Sort](quick-sort.md) - a performant algorithm combined with both [DnC][DnC] and [Randomization](../randomization/overview.md)
* [Non-Comparison Sort](non-comparison-sort.md) - intro to several non-comparison based sorting algorithms

[DnC]: ../divide-and-conquer/overview.md
[insertion-sort]: insertion-sort.md

## References

* [ICS-161 Design and Analysis of Algorithms, UCI](https://www.ics.uci.edu/~eppstein/161/960116.html) - Lecture Notes in Jan 16, 1996
* [CSE-373 Data Structure & Algorithms, UW](https://courses.cs.washington.edu/courses/cse373/17wi/lectures/sorting.pptx) - Lecture Notes, 2017
* [CSC-263 Lecture 13, U of Toronto](http://www.cs.toronto.edu/~tfowler/csc263/Lecture13.pdf) - Lecture notes, 2006
