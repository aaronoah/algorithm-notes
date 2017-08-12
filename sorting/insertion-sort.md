# Insertion Sort

As one of typical [Adaptive Sort](overview.md), _insertion sort_ performs marvelously on list that is partially sorted and it is a great choice for combination with various prevalent sorting algorithms such as [QuickSort](quick-sort.md) and [MergeSort](merge-sort.md).

The fundamental idea is described as: in each iteration of processing the unsorted array (beginning from the original array), remove the first element (&Sopf;) of the unsorted part; in an ascending order of sorted part, check the value of &Sopf; against each element of sorted part and insert it into the appropriate location that smaller sorted elements in its left and larger elements in its right.

## Pseudocode

```
INSERTION_SORT(array) // array is zero-based
  for i := 1 to length(array)
    for j := i to 0
      if array[j-1] > array[j]
        swap array[j] and array[j-1]
```

_Note: if using a dynamic structure to store entries such as [linked list](https://en.wikipedia.org/wiki/Linked_list), you would eliminate multiple times of swapping and only one entry insertion is required for each iteration_.

## Algorithm Analysis

[Insertion Sort][insertion-sort] is a [stable and adaptive sort](overview.md) scheme and a well-formed algorithm in many technical systems. It normally requires &Omicron;(n<sup>2</sup>) compares and swaps but in the best case when the given inputs are nearly sorted, it could only require &Omicron;(n) compares and swaps.

Despite of high efficiency of Insertion Sort in almost sorted list, it consumes many swaps to sort the entire list. [Shell Sort](shell-sort.md) improves upon the deficiencies of [Insertion Sort][insertion-sort].

[insertion-sort]: #insertion-sort
