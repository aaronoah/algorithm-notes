# Divide-and-Conquer Strategy

In the section of [Divide-and-Conquer overview](overview.md), three steps in DnC procedures are discussed. Here in this module, more in-depth discussions will be covered in order to wrap up DnC topic.

## DnC Implications

Although the high-level idea of DnC is essential in resolving many computation problems, it is worth noted that intuitively meaningful algorithm abstraction in DnC pattern in some scenarios are yet worse than the common way methods. (_e.g. simply apply DnC in [matrix multiplication](multiplication.md#matrix-multiplication) does not help improve running time but make it more complex to comprehend._)

In general, the DnC problems are large enough to be divided into sub-problems defines a _**recursive-base**_, when the sub-problems are small enough to stop recursive calls, a _**base-case**_ is defined.

Recurrence relations are a series of equations or inequalities to describe functions in terms of its smaller inputs. Solving the recurrence relations will be the key to unravel the computation complexity of DnC problems.

There are three ways to approach recurrence relations:

1. **substitution method**, a bound is guess and proven by mathematical induction.
2. **recursion-tree method**, recurrences are interpreted as a tree and solved by bounding summations.
3. [**master-method**][master], a mathematical generalized form is given for most of the recurrences, and the most important idea to cover than the other two.

_Note: [**master-method**][master] is only effective when the original problem gets split into sub-problems with equal size. If sub-problems differ in size, the **recursion-method** should be used instead._

[master]: master-method.md

## DnC Examples

There are many divide-and-conquer paradigms in a vast amount of computation tasks. [DnC][DnC] principle is helpful yet imperfect to provide a best algorithm pattern at all-time.

### Merge Sort

As a widely adopted algorithm across various application systems, [Merge Sort](../sorting/merge-sort.md) is simple to evaluate given its identity of a [divide-and-conquer](overview.md) algorithm.

For many beginners of divide-and-conquer paradigm, [Merge Sort](../sorting/merge-sort.md) is a good start.

### Counting Inversions

A pair of keys with random arrangement got compared with the in-order keys to output the number of inversions between the two, called the task of [counting inversions](#counting-inversions). Mathematically speaking, more the difference value between two arrays, more lower the ranking comparisons. It is a widely used algorithm across various subjects such as [voting theory](https://www.princeton.edu/~cuff/voting/theory.html), [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) etc.

The general idea is to recursively compute the similarities of two arrays from index &iukcy; to index &jsercy; accordingly against the left n/2 (&iukcy;,&jsercy; < n/2) of them and the right n/2 (&iukcy;,&jsercy; > n/2) of them. Upon completion of subroutines above, compute the similarities against the whole length (&iukcy; < n/2 < &jsercy;) and sum all the returned results.

### Matrix Multiplication

A novel method [Strassen's Algorithm](multiplication.md) magically improves the matrix multiplication by adoption of [DnC][DnC] pattern. It counters the [naive matrix splitting](multiplication.md) method which fails to decrease the running time on average.

### Quick Sort

Though choosing a _pivot_ in each sub-problem is the major task in [Quick Sort](../sorting/quick-sort.md) algorithm, it utilizes [divide-and-conquer][DnC] in resolving sorting in partitions created in each run.

Its [average-case](../asymptotic-analysis.md) running time &Omicron;(n &sdot; log(n)) maintains the comparison-based sorting lower bound and Quick Sort is a good beginning for [randomization](../randomization/overview.md) techniques.

[DnC]: overview.md
