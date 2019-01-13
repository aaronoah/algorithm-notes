# Shell Sort

[shell sort](#shell-sort) is an [in-place](overview.md), not [stable](overview.md) comparison sort to improve [insertion sort](insertion-sort.md); it is not to be confused with [Unix shell sort](https://www.computerhope.com/unix/usort.htm) which is a command line utility for sorting.

This is a generalization of [insertion sort](insertion-sort.md) which enables distant entries to exchange with each other, compensating the bad performance of [insertion sort](insertion-sort.md) when exchanging entries far apart. Specifically, insertion sort is adopted first to sort on a widely arranged entries, then the less widely arranged entries until the full entries in the last run.

The following steps summarize the shell sort:

1. Pick an initial value for [gap sequence](#gap-sequence) _h_.
2. Divide the inputs into sub-sequences, each with equal gap _h_.
3. Sort the sub-sequences using [insertion sort](insertion-sort.md).
4. Decrease current gpa value _h_ by 1 and repeat the process 2, 3 and 4 until the full inputs are sorted.

Figuratively, suppose to sort a sequence: {35, 33, 42, 10, 14, 19, 27, 44} and the initial [gap sequence](#gap-sequence) is 4; the first run will sort sub-sequences {35, 14}, {33, 19}, {42, 27}, {10, 44} and yield {14, 35}, {19, 33}, {27, 42}, {10, 44}. In the next run if _h_ decreases by 1, the sub-sequences will be {35, 10, 27}, {33, 14, 44}, {42, 19}

<figure style="text-align:center">
  <img src="../images/shell_sort_gap_4.jpg" />
  <figcaption>Figure 1. Shell Sort of Interval 4</figcaption>
</figure>

When the [gap sequence](#gap-sequence) number is reduced down to 1, the [shell sort](#shell-sort) becomes a total [insertion sort](insertion-sort.md) in one run.

## Pseudocode

```
SHELL_SORT(array, gaps)
  for gap in gaps
    for i := gap to 1
      do INSERTION_SORT on entries with gap interval starting from index (gap - i + 1)
```

## Gap Sequences

The running time of [shell sort](#shell-sort) heavily depends on the gap sequences it uses. Every gap sequence that contains 1 outputs the correct results but choosing a different gap sequence would yield a totally distinct shell sort.

Two properties should be known about [shell sort](#shell-sort) before choosing a proper gap sequence:

1. _any_ two numbers within a gap sequence should be prime with each other. (consider a bad gap sequence {1, 3, 5, 6, ...}, a 6-sorted array has common entries when performing 3-sort and render it useless).
2. given two numbers in the gap sequence _g_ and _h_, a g-sorted array after h-sorted remains h-sorted and vice versa.

Finding a proper gap sequence remains an open problem in academia and there are prevalent choices such as Knuth sequence: {1, 4, 13, 40, 121, ...}. It is worth noted that initial gap sequence number evaluates to no more than the length of the inputs and it would perform nothing sorting if not otherwise.

_Formal Def:_

define a **incremental sequence** &Sscr; against a predefined set of variables &Xscr; and locations of sequence number _k_, then

< &Sscr;(&Xscr;, 1), &Sscr;(&Xscr;, 2), ... &Sscr;(&Xscr;, _k_) > would be a gap sequence wherein &Sscr;(&Xscr;, _k_) &les; _n_ (length of inputs), &Sscr;(&Xscr;, 1) = 1

### Knuth Sequence

Invented by a great computer scientist [Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth), this sequence demonstrates a characteristic of arithmetic simplicity, specifically, &Sscr; = (3<sup>k</sup>-1)/2; it produces a sequence {1, 4, 13, 40, 121, ...} that satisfies the above [shell sort](#shell-sort) properties.

### Sedgewick Sequence

In 1986, [Prof. Robert Sedgewick](https://en.wikipedia.org/wiki/Robert_Sedgewick_(computer_scientist)) invented a gap sequence for [shell sort](#shell-sort) {1, 8, 23, 77, 281, ...} that has a optimal computational complexity &Omicron;(n<sup>4/3</sup>); Formally, &Sscr; = 4<sup>k</sup> + 3 &sdot; 2<sup>k-1</sup> + 1, prefixed with 1. It is still the best choice for the gap sequence generator.

## Additional Resources

1. Fastest gap sequence for shell sort? https://stackoverflow.com/questions/2539545/fastest-gap-sequence-for-shell-sort

2. Analysis of Shell Sort and Related Algorithms, R. Sedgewick, Princeton U. http://www.cs.princeton.edu/~rs/shell/paperF.pdf