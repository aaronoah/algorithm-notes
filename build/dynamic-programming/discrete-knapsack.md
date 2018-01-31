# Discrete Knapsack

## Change Problem

A computation problem describes as follow: given an integer amount of _money_ for change and positive integers that representing different denominations _coin<sub>1</sub>, coin<sub>2</sub>, .. coin<sub>n</sub>_, find the minimum number of coins needed to make the change.

_Note: this problem is a [classic discrete knapsack problem](overview.md) with a distinct form._

If [greedy approach](../greedy-algorithms/overview.md) is adopted in the selection process, it would be simple to construct such primitive that in each iteration of remaining _coins_, find the largest denomination and add it in the final tuple of results.

