# Merge Sort

As a typical [DnC](../divide-and-conquer/overview.md) algorithm, MergeSort tries to solve sorting problem in a recursive, distributed way. Its overall algorithm outperforms the [InsertionSort](insertion-sort.md) and canonical [BubbleSort](bubble-sort.md) algorithms.

## Fundamental Ideas

MergeSort algorithm takes the unsorted original array and split it into &Scy; number of sub-arrays, feeding them individually into the algorithm itself for the same sorting purpose.

Then, resolve each sub-problem with the defined minimal length of sub-array. After recursive calls in each layer of division, combining the results of each subroutine to generate the final sorting solution.

_**Note**: the task's aim might varies with scenarios. e.g. a bulk of sorted arrays reside in memory has to merge into an array with randomly filled elements; therefore, the actual implementation is not definite._

## Pseudocode

Though the abstract details are the same, the [top-down MergeSort](#top-down-approach) and [bottom-up MergeSort](#bottom-up-approach) are two different implementations of [MergeSort](#merge-sort). The first one is suitable for education for its simplicity while the second one has a slightly better performance and widely adopted in many libraries.

### Top-down Approach

It is a common practice to use such a recursive approach:

```
TOP_DOWN_MERGE_SORT(array, low, high, new_array)
  if high - low < 2
    return

  middle := (low + high) / 2
  TOP_DOWN_MERGE_SORT(array, low, middle, new_array)
  TOP_DOWN_MERGE_SORT(array, middle, high, new_array)

  TOP_DOWN_MERGE(array, low, middle, high, new_array)

  MERGE(array, low, middle, high, new_array)
```

### Bottom-up Approach

rather than a recursive method in above approach, using a iterative method:

```
BOTTOM_UP_MERGE_SORT(array, new_array)
  for width := 1, width < length(array)
    for i := 0, i < length(array)
      MERGE(array, i, min(i+width, n), min(i+2*width, n), new_array)
      i := i + 2 * width
    width := width * 2
```

and the universal MERGE step:

```
MERGE(array, low, middle, high, new_array)
  i := low
  j := middle
  for k in range (high - low)
    if i < middle and array[i] < array[j]
      new_array[k] = array[i]
      i := i + 1
    else if j < high and array[j] < array[i]
      new_array[k] = array[j]
      j := j + 1
```

## Algorithm Analysis

[MergeSort](#merge-sort) is a [stable](overview.md) sorting scheme that has [average and worst-case](../asymptotic-analysis.md) running times of &Omicron;(n &sdot; log(n)) regardless of the inputs.

It is simple to prove the running complexity by [master method](../divide-and-conquer/master-method.md) &Tau;(n) = 2 &Tau;(n/2) + &Theta;(n)

## Additional References

1. Combining [MergeSort](#merge-sort) and [InsertionSort](insertion-sort.md): https://cs.stackexchange.com/questions/68179/combining-merge-sort-and-insertion-sort
