# Non-Comparison Sort

It is proved in the section of [sorting overview](overview.md) that comparison-based sorting scheme has the best [worst-case](../asymptotic-analysis.md) time of &Omicron;(n &sdot; log n). However, there are certain conditions where sorting algorithms could be designed to have linear time complexity. They are further discussed here in this module:

## Counting Sort

Unlike sorting on randomly distributed inputs in the context of most comparison-based sorting, [counting sort](#counting-sort) assumes that inputs are non-negative integers; if inputs are alphanumeric or mixed with different character sets, it is still possible to map their respective values to same weight integers before sorting is performed.

_Fundamental Idea_:

There are _n_ inputs ranging from 0 to k; then for each input &xscr;, determine the number of entries that are less than or equal to &xscr; in order to put &xscr; into the right location. (e.g. if 8 entries less than (or equal to) &xscr;, put &xscr; into the 9<sup>th</sup> slot).

Specifically, first use an array of length _k_ to store the occurrences of all entries individually; then for each index i of array, summing up the values of which the indexes smaller than i; finally, insert entries into positions indicated by the occurrence array.

```
COUNTING_SORT(array, result, k)
  C[0..k] = new array
  for i := 0 to k
    C[i] := 0
  for j := 0 to length(array) - 1
    C[array[j]]++
  for i := 1 to k
    C[i] := C[i] + C[i-1]
  for j := length(array) to 1
    result[--C[array[j]]] = array[j]
```

_Algorithm Analysis_:

The total amount of operations is 2k + 2n; according to [asymptotic notations](../asymptotic-analysis.md), time complexity is &Theta;(k + n) and in real scenarios where k = &Theta;(n), the total running time is &Theta;(n).

It is worthy of notion that [counting sort](#counting-sort) is a [stable sort](overview.md) and provides a solid foundation for [radix sort](#radix-sort) as a subroutine.

## Bucket Sort

Bucket Sort assumes the inputs are uniformly distributed on the universe in order to achieve time complexity of about &Omicron;(n);

The fundamental idea is to partition the inputs range into segments of inputs with equal length, called _bucket_; traverse the entire inputs and map individual entry to its relative _bucket_; apply [insertion sort](insertion-sort.md) to entries in each bucket then traverse the buckets to list all the entries in order.

## Radix Sort

Same as the [counting sort](#counting-sort), radix sort is a non-comparative integer sorting algorithm while requiring a [stable sort](overview.md) subroutine such as counting sort during the process of sorting each digit place numbers.

The fundamental idea is that starting from location of the [least significant bit (LSB)](https://en.wikipedia.org/wiki/Least_significant_bit) to the [most significant bit (MSB)](https://en.wikipedia.org/wiki/Most_significant_bit) (if higher digit places are empty, fill up with zeros), all digits in that location of all input numbers are sorted.

An example: given input sequence {329, 457, 657, 839, 436, 720, 355}; sort the bit numbers, then the tens place finally the hundreds, sorting completes.

<figure style="text-align:center">
  <img src="../images/radix-sort.jpg" />
  <figcaption>Figure 1. Radix Sort Example</figcaption>
</figure>

A variant of this algorithm (MSB radix sort) is to start sorting the bit place from MSB to LSB however it is more efficient to adopt the basic one (LSB radix sort) since the _MSB radix sort_ is a recursive approach but _LSB radix sort_ is non-recursive.

_Note: the reason of performing recursion in MSB radix sort is to assist memoization of previous computation results. (e.g. sorting a digit place with a 2 and a 3 does not guarantee the same ordering in those positions after sorting completion)_.

_Algorithm Analysis_:

Radix sort could sort numbers of not large digit places in a promising speed; if sorting subroutine takes &Theta;(n + k), where _n_ is the number of inputs, _k_ is the number of possible values each digit can take.

Then, for _d_ number of sorting subroutines (_d_ is the digit amount of the largest number), the total time complexity would be &Theta;(d(n + k)); since the sorting subroutine only deals with single digit, it is intuitive that the largest value of _k_ is 10 ranging from 0 to 9.

When _d_ is relatively smaller compared to _k_, the running time is &Omicron;(n + k); when _d_ is far larger than _k_, which is common in large-scale computing problems, the time complexity is &Omicron;(d &sdot; n).