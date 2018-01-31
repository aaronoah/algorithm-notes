# Divide-and-Conquer (DnC) Overview

Recursively, many algorithms try to call themselves multiple times for solving tightly relevant sub-problems.

The DnC paradigm takes the following steps:

1. DIVIDE original problem into sub-problems
2. CONQUER each sub-problem recursively
3. (*) COMBINE solutions for sub-problem into one for the original problem

    _**Note**: some problems don't have combination phase; for instance, BinarySearch will search for specified element in either the left (n /2) or the right (n /2) of an array and return that element if found._

## Table of Contents

* [Multiplication](multiplication.md) - chapter about integer multiplication, matrix multiplication and polynomial multiplication.
* [Master Method](master-method.md) - a generalized form of mathematical interpretation is given for DnC problems.
* [DnC Strategy](dnc-strategy.md) - several different strategies for various problems will be covered.
