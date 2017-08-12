# Selection Sort

selection sort is an introductory level sorting scheme and its idea is straightforward: find the minimal number in each traverse of the unsorted part of list and replace it with first element on unsorted part of list to become a member of the sorted list, until the unsorted list is empty.

## Pseudocode

```
SELECTION_SORT(array, length)
  for i := 1 to n - 1
    min := i
    for j := i + 1 to n
      if array[j] < array[min]
        min := j
      if min != i
        swap array[i] and array[min]
```

_Note: the comparison step between index i and min value is complementary to improve the efficiency in case the element itself has to swap with itself._

## Algorithm Analysis

[selection sort](#selection-sort) takes (&Nscr; - 1) + (&Nscr; - 2) + ... + 0 &ap; &Nscr;<sup>2</sup> / 2 compares and &Nscr; exchanges.

No matter how the presortedness of inputs, the algorithm running time is quadratic. It is worth noted that selection sort scheme should not be used in most of scenarios except for cases that desire minimal cost of element exchanges. Therefore, according to [asymptotic notation](../asymptotic-analysis.md), selection sort [worst-case]() running time is &Omicron;(n<sup>2</sup>).
