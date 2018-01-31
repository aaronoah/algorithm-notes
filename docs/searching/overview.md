# Searching

Modern technology development has led to a vast amount of information available to the public. It is a fundamental ability to _search_ through the bulky data sets over the Internet for specified piece of information. Various of topics related to searching will be discussed further.

## Symbol Table

An abstract searching mechanism that a _value_ entry is stored and later retrieved by a corresponding _key_ is a [symbol table][symbol-table], also known as _dictionary_. There are huge amount of keys and information for use in Internet and numerous applications such as symbol table in [compiler design](http://www.cs.cornell.edu/courses/cs412/2008sp/lectures/lec12.pdf).

The main purpose of this data structure is to associate a _value_ with a _key_ and be able to search the _value_ by its _key_. A formal definition of [symbol table][symbol-table]: a _key-value_ pairs that supports two operations: _Insert_ a pair into the table and _Search_ for the _value_ with a given _key_.

Technically, the _keys_ are unique and duplicate _keys_ may result in inconsistent searching operations. And _values_ may collide with different associative _keys_ such as two customers in a commercial database have the same DOB.

_Note: a [symbol table][symbol-table] is a conceptual structure that supports the searching operation and it indicates dynamic key-value pairs during such operation; if searching for a customer's name given his ID, the ID is the **key**, if searching for the ID of a customer given the name, the name is the **key**_.

## Guidelines

Noting that the [symbol table][symbol-table] could have _key-value_ pairs in which key equals the value; the _searching_ operation would return either one, multiple or no results and this operation takes advantage of the principle of [symbol table][symbol-table].

A plenty of data structures such as List, Array, Tree, Graph, Hash Table are built searching operation foundations. It is worth noted that List, often refers to [LinkedList](https://en.wikipedia.org/wiki/Linked_list), is designed to have multiple containers of specific data objects connected to form a dynamic structure, while Array is a bulk of adjacent cells aligned in memory to form a static structure. _(when locating i<sup>th</sup> element in Array structure, address(Array[i]) = address(Array[0]) + i * sizeof(Array object), thus it takes &Omicron;(1) time)_

_Search Operations_:

* SEARCH: find the specified element within the set of data.
* SELECT: locate the [i<sup>th</sup> order statistic](https://en.wikipedia.org/wiki/Order_statistic)) within a possibly unordered set of data.
* MIN/MAX: find the minimum or maximum value among the values of the set of data.
* PREDECESSOR/SUCCESSOR: locate the immediate neighbors that are closest to the designated _key_ in terms of values. PREDECESSOR(&Xscr;) is the maximal value closest to &Xscr; while SUCCESSOR(&Xscr;) is the minimal value closest to &Xscr;.
* RANK: count the number of elements that are less than or equal to the specified _key_.

## Comparison-based Searching

### Searching Lower Bound

## Table of Contents

* [Hash Table](hash-table.md) - an _associate array_ structure to assist in the processing of searching, insertion and deletion.
* [Graph Search](graph-search.md) - graph searching primitives that are commonly used.
* [Binary Search](binary-search.md) - searching _key_s by means of [DnC](../divide-and-conquer/overview.md) principle.
* [String Matching](string-matching.md) - searching characters or substrings in input strings, involving discussions of [regular expression](string-matching.md) and [KMP algorithm](string-matching.md), etc.

[symbol-table]: #symbol-table
