# Bubble Sort

[Bubble Sort](#bubble-sort) is a simple yet straightforward swap sorting primitive and its principle is the same as what you might expect from a bubble surfacing up and down in the water.

## Pseudocode

A naive implementation would be as follow to bubble up the biggest number to the rightmost position in each run for computing the ascending sequence and bubble up the smallest number to the rightmost position in each run for computing the descending sequence:

```
BUBBLE_SORT(array)
  for i := 1 to length(array)
    for j := 1 to length(array) - i
      if array[j] > array[j+1]
        swap(array[j], array[j+1])
```

To improve upon that, a **sentinel** is introduced so as to resolve useless iterations and comparisons in partially sorted inputs:

```
BUBBLE_SORT(array)
  sentinel := 1
  for i := 1 to length(array)
    if sentinel = 1
     break
    for j := 1 to length(array) - i
      if array[j] > array[j+1]
        swap(array[j], array[j+1])
        sentinel := 0
```

## Algorithm Analysis

[bubble sort](#bubble-sort) is elementary yet simple to evaluate; it yields a [best-case](../asymptotic-analysis.md) scenario of &Omicron;(n) for partially sorted arrays and [worst-case](../asymptotic-analysis.md) of &Omicron;(n<sup>2</sup>)