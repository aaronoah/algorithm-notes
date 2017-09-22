# Heap Sort

Based on a typical [heap](../tree/heap.md) data structure, Heap Sort is an [in-place, not stable comparison-baed sorting](overview.md) algorithm and can be thought of as a improved version of [selection sort](selection-sort.md) algorithm.

## Fundamental Ideas

Initially, a [BUILD-MAX-HEAP](../tree/heap.md) is called upon a randomly distributed inputs to setup a [max-heap](../tree/heap.md). Now that the topmost root key must be the largest among the heap, extract that key to a sorted array and restore the heap property using [MAX-HEAPIFY](../tree/heap.md) operation. Repeat the procedures of extraction and adjustment till the heap is empty, the sorted array is formed.

In each heap restoration process, instead of [selection sort](selection-sort.md) method of locating the maximum or minimum key within the inputs in linear time, Heap Sort uses [MAX-HEAPIFY](../tree/heap.md) operation to reduce time complexity to logarithmic bound.

## Pseudocode

The following code transforms a randomly distributed array into an ascending entry array.

```
HEAP_SORT(A)
  BUILD_MAX_HEAP(A)
  for i = length(A) to 2
    swap A[1] and A[i]
    A.heap_size = A.heap_size - 1
    MAX_HEAPIFY(A, i)
```

## Algorithm Analysis

Given a n-size inputs, there is a &Omicron;(n) estimate on [BUILD_MAX_HEAP](../tree/heap.md) operation; And for each input entry, a [MAX_HEAPIFY](../tree/heap.md) is expected to perform and thus costs &Omicron;(n &sdot; log(n)) in total.

Since the [Heap Sort](#heap-sort) is also a [comparison-based sorting](overview.md) that has proven with a lower bound &Omega;(n &sdot; log(n)), the more tighter bound for Heap Sort will be &Theta;(n &sdot; log(n)).

## Additional References

1. Why is Heap Sort used? https://www.quora.com/Why-is-heap-sort-used
