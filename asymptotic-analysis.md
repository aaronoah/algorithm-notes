# Asymptotic Analysis

This is a theoretical notation of algorithm analysis with a formal mathematical foundation.

## Why Analyzing Algorithms?

To optimize the performance during the process from inputs to outputs. To become a better Software/Hardware developer in any fields of computer science. Improve your analytical thinking with programming abilities and many more.

A quote from _The Design and Analysis of Algorithms_, 1974, that:

> Perhaps the most important principle for the good algorithm designer is to refuse to be content.

Upon leaving the note above, we know that constant assessments and improvements are required for the algorithm designers to advance their goals in research or work.

_Note: algorithm itself is **programming language-agnostic** and the [pseudocode](https://en.wikipedia.org/wiki/Pseudocode) is a communicative tool for algorithm's descriptive purposes_.

## Machine Model

**Resources** (memory, CPU and disk spaces) are what we take into account as analyzing the algorithms are ongoing and most of the time we care about the running time of a piece of program in a general purpose computing machine and a generalized model comes into play.

**RAM** ([Random Access Machine](https://www.youtube.com/watch?v=by1HmASLHkM)) with a single core and execute one instruction a time is a proper model for analyzing algorithms. And it will bypass the hierarchy modeling of common memory/cache of real computers for analysis simplicity.

## Factors of Algorithm Analysis

To devise a _FAST_ algorithm in specific context, we should be expecting a slow growth of the [worst-case](#worst-case) running time with the input size, and it gives rise to a corresponding [Big-Oh](#big-oh-notation) interpretation.

### Worst-Case

Why do we care about worst-case scenario?
1. Worst-case running time provides an absolute uppper bound given the input size _n_, no even worse case could happen.
2. Worst-case often happens. For instance, a special entry of info is missing upon database querying, then query process takes the worst-case running time.
3. [Average-Case](#average-case) usually performs as much bad as the Worst-Case: given an array with random numbers, how long it takes to determine the place of _A[1..j-1]_ to insert _A[j]_ into? In average, half of _A[1..j-1]_ less than _A[j]_ and half larger than _A[j]_, thus the comparison time reduces by 2 but the resulting average-case running time still is a proportion of a quadratic function.

### Average-Case

It is useful though rare for the average-case scenario comes into play. E.g. In situations where we require statistical, probability analysis and randomized algorithms.

### Asymptotic Notations

Asymptotic analysis is a _**Sweet Spot**_ for high-level reasoning about algorithms and a good enough technique to suppress details of less important **Resources** such as computer architecture, language spec and compiler implementations.

It is designed to focus on understanding large-scale problems for its nature in addressing a "asymptotic" alike representations. For instance, the mathematical [Big-Oh](#big-oh-notation) notation helps describe how algorithm running time grows with input size approximating to Infinity; likewise, it could also formalize approximately how many possible connected edges there are given a fixed number of vertices of a graph structure.

_**Note**_: _suppress constant factors (too system dependent) and lower-order terms (irrelevant terms for large inputs) are the best practices in analysis_

#### Big-Oh Notation

[Big-Oh Notation](#big-oh-notation) is the most commonly used asymptotic notations since most of the time we care about the upper bound, in other words, the [worst-case](#worst-case) of the algorithm running time.

Formal Def:
&Tau;(n) = &Omicron;(&fnof;(n))
_iff_ &exist; &scy;,n<sub>0</sub>
such that &Tau;(n) &les; &scy; &sdot; &fnof;(n) for &forall; n &ges; n<sub>0</sub>

#### Big-Omega Notation

[Big-Omega](#big-omega-notation) often describes the best case running time given the algorithm but normally we care the least of it during the analysis process.

Formal Def:
&Tau;(n) = &Omega;(&fnof;(n)) _iff_
&exist; &scy;,n<sub>0</sub>
such that
&Tau;(n) &ges; &scy; &sdot; &fnof;(n) for &forall; n &ges; n<sub>0</sub>

#### Big-Theta Notation

[Big-Theta](#big-theta-notation) serves as a supplement to the [Big-Oh](#big-oh-notation) for an exhaustive prediction in terms of algorithm analysis.

Formal Def: &Tau;(n) = &Theta;(&fnof;(n)) _iff_ &Tau;(n) = &Omicron;(&fnof;(n)) and &Tau;(n) = &Omega;(&fnof;(n))

It is a common error to use &Omicron; instead of &Theta; to denote the &Tau;(n) for specific algorithms. For instance, the [MergeSort](sorting/merge-sort.md) has &scy;n &sdot; log(n) + &scy;n operations in total. Instead of saying it bounds to &Theta;(n &sdot; log(n)), many would intuitively claim it bounds to &Omicron;(n &sdot; log(n)); both statements are true but the former one is a stronger claim.

<figure>
<img src="http://draperg.cis.byuh.edu/archive/winter2012/cs301/lectures/lecture06/big_oh_graphs.png" />
<figcaption>Figure 1. Graphic representations regarding Big-Oh, Big-Omega and Big-Theta</figcaption>
</figure>

### Order of Growth

There are many commonly seen order of growth functions describing the computation complexity of algorithms:

* **Constant**: number of operations are nearly stable even if with growth of inputs processing; _e.g. &Omicron;(1), &Omega;(1) and &Theta;(1)_.
* **Linear**: number of operations grows linearly with number of inputs; _e.g. &Omicron;(n), &Omega;(n), &Theta;(n)_.
* **Logarithmic**: number of operations grows slowly with number of inputs; _e.g. &Omicron;(log(n)), &Omega;(log(n)), &Theta;(log(n))_.
* **Linearithmic** (combo of Linear and Logarithmic): number of operations grows faster than linear but slower than quadratic; _e.g. &Omicron;(n &sdot; log n), &Omega;(n &sdot; log n), &Theta;(n &sdot; log n)_.
* **Polynomial**: running times in form of n<sup>k</sup> where k is integers.
    * **Quadratic**: number of operations grows in a power of 2 with the number of inputs; _e.g. &Omicron;(n<sup>2</sup>), &Omega;(n<sup>2</sup>), &Theta;(n<sup>2</sup>)_.
    * **Cubic**: number of operations grows in a power of 3 with the number of inputs; _e.g. &Omicron;(n<sup>3</sup>), &Omega;(n<sup>3</sup>), &Theta;(n<sup>3</sup>)_.
* **Exponential**: number of operations grows exponentially with the number of inputs; _e.g. &Omicron;(2<sup>n</sup>), &Omega;(2<sup>n</sup>), &Theta;(2<sup>n</sup>)_.

<figure style="text-align:center">
  <img src="images/order_of_growth.png" />
  <figcaption>Figure 2. Order of Growth Diagram</figcaption>
</figure>

---

## Additional References

1. MIT Big-Oh Notation Intro, http://web.mit.edu/16.070/www/lecture/big_o.pdf

2. Big O versus Big Omega, https://www.programmerinterview.com/index.php/data-structures/big-o-versus-big-omega-notations/
