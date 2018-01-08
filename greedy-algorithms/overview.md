# Greedy Algorithms

Using [dynamic programming](../dynamic-programming) in most of the scenarios could be an overkill for optimization problems. A more efficient and simpler method could be adopted instead, which is [greedy algorithms](https://en.wikipedia.org/wiki/Greedy_algorithm). It will choose the best move in each step of solving sub-problems, in other words, a local optimal solution is made every time and hopefully it leads to the global optimal solution at the end.

## Activity Selection Problem

Assume there are _n_ activities {a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>} that all use the same room which is only available for one activity at a time. Each activity has a _starting time_ s<sub>i</sub> and a _ending time_ f<sub>i</sub>. If two activities have no overlapping time frames then they are **compatible**, and a maximal compatible set of activities is required to compute at the end.

It is reasonable to solve this problem using [dynamic programming](../dynamic-programming/overview.md) approach with optimal substructure and solution scheme. However, there is an easy way to conquer this problem using [greedy](https://en.wikipedia.org/wiki/Greedy_algorithm) approach.

Intuitively, an activity is chosen that ends the first and spare as much time as possible for the rest of activities (there might be other greedy approaches, this only serves as an example). After the first greedy choice is made, the sub-problem needs to be considered that finding **compatible** activities following and by continuing doing so until the set is empty.

## Table of Contents

Though few scenarios can adopt greedy approaches, there are some proven interesting example problems solved using greedy approach:

* [Fractional Knapsack](fractional-knapsack.md) - classic knapsack problem with revision that items can be fractioned.
* [Huffman Coding](huffman-coding.md) - an efficient way to compress binary data by variable length coding.