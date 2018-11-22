# Randomization

The history of mankind using the notion of _random_ is widely reflected in gambling or insurance and in the fields of computer science as well through a number of analytic examples.

In the algorithm design, [randomization](#randomization) plays a pivot role in probabilistic algorithm designs in two ways of which we care about:

* Classic algoritm is feeded with randomly generated inputs, in other words, the _average_ inputs are studied to offer [_**average-case analysis**_](../asymptotic-analysis.md)

* [**Worst-case**](../asymptotic-analysis.md) inputs are provided as always to the algorithm in the classical way, but processed in a random manner. The internal execution model dealing with randomization is a typical [**randomized algorithm**][randomized].

## Table of Contents

* [Discrete Probability](discrete-probability.md) - probability analysis, indicator random variable and several statistics definitions covered.
* [Randomized Algorithms][randomized] - median-finding problem, i<sup>th</sup> order statistic finding problem are analyzed and solved randomly and deterministic.
* [Reservoir Sampling](reservoir-sampling.md) - an introduction to a common technique in data processing.

[randomized]: randomized-algorithms.md
