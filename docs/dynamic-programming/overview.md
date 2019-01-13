# Dynamic Programming

In the fields of computer science, economics, managerial sciences, mathematics and bioinformatics, [dynamic programming][dynamic] or dynamic optimization is similar to [divide-and-conquer][DnC] principle as to decompose a complex problem into smaller sub-problems.

## Fundamental Idea

In contrast to the paradigm of [DnC][DnC] that sub-problems are independent, dynamic programming is adopted to solve interleaved sub-problems wherein multiple sub-problems might have common smaller sub-problems. And for each repetitive sub-problem, [dynamic programming][dynamic] would store and reuse the solution when it was solved the first time (also known as [_memoization_](https://en.wikipedia.org/wiki/Memoization)), programming solutions all together.

The typical [dynamic programming][dynamic] algorithm is developed in steps follow:

1. Characterize the _optimal_ sub-structures along with possible moves. (think of it as finding a DAG for a solution path)
2. Define the recurrence relations of sub-problems.
3. Compute recursively or iteratively in a _bottom-up_ fashion or _top-down_ with [_memoization_](https://en.wikipedia.org/wiki/Memoization) fashion.
4. Construct an overall _optimal_ solution or combining solutions of sub-problems.

_Noted that the word **programming** does not stand for **computer programming** but a tabulation method that was invented by [R. Bellman](https://en.wikipedia.org/wiki/Richard_E._Bellman)_.

## Comparing with [Greedy Algorithms][greedy]

It is often confusing to determine if the programming logic is built on [dynamic programming][dynamic] or [greedy algorithms][greedy]. Both are adopted in favor of tackling _optimization problem_, and [dynamic programming][dynamic] seeks and combines the previous solutions for sub-problems to yield the final result while [greedy algorithms][greedy] chooses locally optimal solution in each run and not guarantee to have the optimal result.

For instance, in a [coin change problem](https://en.wikipedia.org/wiki/Change-making_problem) of finding a minimum number of coins with certain denominations added up to a specified amount, [dynamic programming][dynamic] is a killer solution than using [greedy algorithms][greedy] in that:

given a set of denominations: 1, 4, 5, 15, 20 and the specified amount 23; the [dynamic programming][dynamic] would yield an optimal solution of 15 + 4 + 4 while the [greedy algorithms][greedy] offers a non-optimal one 20 + 1 + 1 + 1.

wherein, [greedy algorithms][greedy] picks the largest one in the set of coins from the first run; [dynamic programming][dynamic] takes into account the solutions to each small sub-problem that are related to each other during iterations.

## Table of Contents

The following example questions can be categorized into [dynamic programming][dynamic] type:

* [Fibonacci Numbers](fibonacci-numbers.md) - a topic referring to [Fibonacci sequence](https://en.wikipedia.org/wiki/Fibonacci_number) that to find a i<sup>th</sup> such number.
* [Matrix-Chain Multiplication](matrix-chain-multiplication.md) - solving the matrix dot multiplication in an most efficient way by least number of scalar multiplications in total.
* [LCS Problem](lcs-problem.md) - a practical problem found in many scenarios such as DNA sequences detection.
* [Discrete Knapsack](discrete-knapsack.md) - knapsack problem in a discrete version.

[dynamic]: #dynamic-programming
[greedy]: ../greedy-algorithms/overview.md
[DnC]: ../divide-and-conquer/overview.md
