# Hash Table

This section concerns [Hash Table][hash-table] data structure and its relevant hash functions designs. And it's an improved version of [Direct-Access Table](#direct-access-table) for operational efficiency.

## Direct-Access Table

As an inherited example of [Symbol Table](overview.md), [Direct-Access Table](#direct-access-table) is satisfactory if given a small universe &Uscr; of _keys_ for its implementation simplicity and effectiveness.

Formal Def:

Suppose distinct m _keys_ are taken from &Uscr; &sube; {0, 1, ..., n}, setup an array T[0, 1, ...m-1]:

<figure style="text-align:center">
  <img src="../images/direct_access_table.png" />
  <figcaption>Figure 1. Direct-Access Table Mathematical Representation</figcaption>
</figure>

wherein every position in array T is called a _slot_. It is expected to have only &Theta;(1) access time but if the range of _keys_ is too large, e.g. 64-bit numbers which have over trillions of different _keys_, the [direct-access table](#direct-access-table) may be overwhelmed in memory usage as well as entry access time. It is a poor choice in the context of Internet data size. Thus, the [Hash Table][hash-table] is introduced.

## Design Idea

[Hash Table][hash-table] is an extended array structure that associate _keys_ with _values_ that is dynamically resizable on demand. It is designed to combine the good qualities of [List](https://en.wikipedia.org/wiki/List_(abstract_data_type)) and [Array](https://en.wikipedia.org/wiki/Array_data_structure) data structures.

Suppose given an evolving set &Sscr; from global universe &Uscr;.

* [List](https://en.wikipedia.org/wiki/List_(abstract_data_type)) only requires &Theta;(|&Sscr;|) space but lookup time &Theta;(|&Sscr;|) as well.
* [Array](https://en.wikipedia.org/wiki/Array_data_structure) only requires &Omicron;(1) for lookup time but &Theta;(|&Uscr;|) space.

[Hash Table][hash-table] possesses both the small space of storage &Omicron;(|&Sscr;|) and swift entry access of &Omicron;(1) optimally.

In order to support three distinct operations of [Hash Table][hash-table]: **INSERTION** of new record, **DELETE** existing record and **LOOKUP** for a specified record, [Hash Table][hash-table] is built in several steps:

1. decide a n that is the number of "buckets" for storing entries; (might be dynamically extensible if |&Sscr;| is variant).

2. choose a [hash function](#hash-function) &hscr;: &Uscr; &rarr; {0,1,2, .., n-1}

3. store entry &xscr; in array A[&hscr;(&xscr;)]

_Note: if the record does not exist, **INSERTION** of new entries will complete but **DELETE** will fail; if the record exists, **INSERTION** of new entries will override the existing values and **DELETE** will succeed._

What if the "bucket" location has already been occupied when trying to insert a new entry? In other words, a [hash collision](#hash-collision) happens. Generally, there are two approaches, [(separate) chaining](#separate-chaining) and [open-addressing](#open-addressing), in resolving this situation.

## Hash Collision

_Note: hash collision always happens, there is never a "perfect" hash function ever discovered to have no collisions during entry insertion_.

### Load Factor

Define a [load factor](#load-factor) (&alpha;) as a hashing performance metric for [hash table][hash-table] &Tau;:

&alpha; = n / m, where n is the total number of elements, m is the number of buckets in [hash table][hash-table] for storing elements. The value of &alpha; can vary as bigger than 1, equal to 1 and less than 1; when &alpha; is far larger than 1, the hash table is hence overloaded and need to expand itself by the techniques introduced in [table doubling](#table-doubling).

The [average-case](../asymptotic-analysis.md) performance of hashing depends on how well the &hscr; function distribute n _keys_ in m slots. Hence, assuming that bucket position each element is hashed into is _independent_ with each other and equally likely any of m slots would be chosen as the bucket, then

_**simple uniform hashing**_:

For &jsercy; = 0, 1, ..., m-1, let's denote the length of the list &Tau;[&jsercy;] by n<sub>&jsercy;</sub>, so that n = n<sub>0</sub> + n<sub>1</sub> + .. + n<sub>m-1</sub>. The **expected value** of n<sub>&jsercy;</sub> is E[n<sub>j</sub>] = &alpha; = n/m.

And the following content provides practices on the basis of such term.

### (Separate) Chaining

In [chaining](#chaining) method, all entries with same hash values are chained together in a [LinkedList][linkedlist]; Specifically, either a pointer exists in a bucket of the [hash table][hash-table] which points to the LinkedList (Singly or Doubly Linked list) of all entries hashed to that bucket, or there is only a NIL in that bucket.

LOOKUP costs &Theta;(1 + &alpha;) in [chaining](#chaining) version of [Hash Table][hash-table]. INSERTION operation in this structure takes [worst-case](../asymptotic-analysis.md) running time of &Omicron;(1), while the DELETION might takes up to &Omicron;(n) if all entries hashed into one bucket; if using the doubly [LinkedList][linkedlist], DELETION may speed up.

### Open Addressing

Although it is possible for [(separate) chaining](#separate-chaining) method to have number of buckets smaller than the total number of elements to store, [open addressing](#open-addressing) must be kept with enough extra spaces in [hash table][hash-table] buckets (m &ges; n, &alpha; &les; 1).

In other words, all elements are stored in buckets and one entry per bucket. While it is possible for such hash table to fill up the entire buckets, [open addressing](#open-addressing) method saves memory occupation by [pointers](https://en.wikipedia.org/wiki/Pointer) to allocate more buckets, drastically minimizing hash collisions and improving searching speed.

In order to INSERT element into the hash table, [open addressing](#open-addressing) requires continuous buckets examinations, which is termed **probe**, until an empty bucket is located;

_probe sequence_: to make INSERTION operation successful, for each _key_ k, there is a length m **probe sequence**:

< h(k,0), h(k, 1), ..., h(k, m-1) >

wherein each [hash function](#hash-function) generates a distinct position within the range of buckets. There are three major _probing_ techniques in which _probe sequence_ is produced in different manners.

_Note: when performing DELETE operation, the designated entry should be labeled "deleted" in case of further DELETE operation failure. (e.g. k<sub>2</sub> is inserted after probing the location of k<sub>1</sub>, if k<sub>1</sub> is deleted to recover an empty bucket, there is no way to know beforehand whether k<sub>2</sub> has been inserted. Then, the further SEARCH and DELETE operation of k<sub>2</sub> will fail)_

* Linear Probing

Given an auxiliary hash function &hscr;<sup>'</sup>: &Uscr; -> {0, 1, ..., m-1}, then linear probing would use:

&hscr;(k, i) = (&hscr;<sup>'</sup>(k) + i) mod m

that before INSERTION, first probing the bucket &Tau;[&hscr;<sup>'</sup>(k)], and &Tau;[&hscr;<sup>'</sup>(k) + 1],... till the &Tau;[&hscr;<sup>'</sup>(k) - 1]; to be noted that the initial probing position determines the entire possible sequence.

* Quadratic Probing

Under the same premise of [linear probing](#linear-probing), quadratic probing adopts a better strategy:

&hscr;(k, i) = (&hscr;<sup>'</sup>(k) + &cscr;<sub>1</sub> &sdot; i + &cscr;<sub>2</sub> &sdot; i<sup>2</sup>) mod m

wherein &cscr;<sub>1</sub> and &cscr;<sub>2</sub> are positive constants, i = 0, 1, ..., m-1

instead of occupying large portions of adjacent buckets by using [linear probing](#linear-probing), quadratic probing leads to a more dispersed distribution of elements.

* Double Hashing

This is known as the best strategy of the three in [open addressing](#open-addressing) method;

&hscr;(k, i) = (&hscr;<sub>1</sub>(k) + i &sdot; &hscr;<sub>2</sub>(k)) mod m

where in both &hscr;<sub>1</sub> and &hscr;<sub>2</sub> are auxiliary hash functions; in order to search the whole hash table, value of &hscr;<sub>2</sub> has to be relatively prime to the hash table size m. And it results in a &Theta;(m<sup>2</sup>) of probing sequence for each _key_ k, approximating the _optimal_ **simple uniform hashing** that for each _key_ there is m! number of _probe sequence_ permutations.

---

## Hash Function

What makes a "good" hash function? it should have properties of _spreading data out_ uniformly in the [hash table](#hash-table) and simple to compute and evaluate.

A common practice in hash function is to transform the universe of _keys_ into _natural numbers_ {0, 1, 2, ...} and process such numbers to construct the hash function.

In designing the hash function &hscr; against key _k_, there are genuinely three methods in which first two are heuristic while the last one is an randomized technique.

### Division Method

By taking modular arithmetic in the following form, the key _k_is hashed into one of m buckets of the [hash table][hash-table]:

&hscr;(_k_) = _k_ mod _m_, where _m_ &ne; 2<sup>p</sup>, p is natural number.

_Note: it is wise to choose a [prime number](http://whatis.techtarget.com/definition/prime-number) as the value of m, this method is practical but inconvenient to find a prime number_.

### Multiplication Method

There are four steps to construct a multiplication hashing method:

1. multiply _k_ with a constant _A_ (0 < _A_ < 1). (all of length _w_ in terms of word length)
2. extract the decimal part of the previous result.
3. multiply _m_ with the previous result.
4. round down to an integer and obtain the hash value.

&hscr;(_k_) = &lfloor; m &sdot; (_k_A mod 1) &rfloor;

Generally, this method outperforms the [division method](#division-method). If _m_ is a power of 2, it is easier to compute the hash simply by shifting bits.

<figure style="text-align:center">
  <img src="../images/multiplication-hashing.jpg" />
  <figcaption>Figure 2. Multiplication Hashing Method</figcaption>
</figure>

### Universal Hashing

(this section is not yet covered)

## Table Doubling

When the number of elements exceeds the number of buckets (assume chaining is not used), the hash table needs to grow its size to not slow down the access speed. Similar as when the number of elements are far less than the number of buckets, the hash table needs to shrink its size to save memory space.

The goal is to make sure &Theta;(n) = m whenever the table shrinks or grows. Then, how fast should it grow and shrink?

Suppose it grows from m to m+1, which means there is rebuild of hash table in every step of insertion, in total: &Theta;(1 + 2 + 3 + ... + n) = &Theta;(n<sup>2</sup>), not good.

What about grow it to its double size? e.g. m to 2m, which means there is only rebuild of hash table in 2<sup>i</sup>th step (i is the number of insertion operation), in total: &Theta;(1 + 2 + 4 + ... + n) = &Theta;(n) (n is a power of 2). There are few inserts cause linear time to rebuild the hash table while the overall average time would be &Theta;(1) (see [amortized analysis](https://stackoverflow.com/questions/11102585/what-is-amortized-analysis-of-algorithms))

For table shrinkage, if applying the similar rule to shrink the table size to its half, there will have problems when the n exceeds m by 1 then delete that new element (first double the table size then resize to original). Therefore, in order to avoid that frequent memory modification pattern, the table will shrink to half its size when n = m / 4

---

## Examples

Various programming problems borrow solutions from [Hash Table][hash-table] implementations to increase productivity.

### De-Duplication

Given a _stream_ of objects, say real time data from WEB, the goal is to remove duplicates and to keep track of unique object occurrence.

If a new object arrives, check if it exists in current hash table, insert it if not present even with same hash _key_ and drop it otherwise.

It is applicable in scenarios such as reporting unique visitors to website or avoid repeated searching results by end users.

---

### [The 2-SUM Problem](https://leetcode.com/articles/two-sum/#approach-2-two-pass-hash-table-accepted)

Given an unsorted array A of n integers and a target sum t, determine whether or not there are two numbers x, y in A with x + y = t.

A naive solution may be to use exhaustive search in two encapsulated loops of &Theta;(n<sup>2</sup>). And to improve slightly upon that, applying a [comparison-based sort](overview.md) such as [MergeSort](../sorting/merge-sort.md) piggybacking a [binary-search](binary-search.md) for t - x given every x would have a &Theta;(n &sdot; log n) complexity.

Overall, a killer solution is by using the concept of [Hash Table][hash-table]. Insert values of A into a hash table and for each value x in the table, search the t - x in &Theta;(n) time.

---

### Java 8 HashMap

> _reference_:
> http://www.nagarro.com/de/perspectives/post/24/performance-improvement-for-hashmap-in-java-8

Hash collisions in hash table data structures have significant impact on performance of LOOKUP operation as to increase the [worst-case](../asymptotic-analysis.md) running time from &Omicron;(1) to &Omicron;(n).

To improve upon that, Java8 spec of HashMap implementations requires the buckets containing colliding keys should store entries in a balanced tree instead of linked list. Hence, the searching operation takes no more than &Omicron;(log(n)) in general.

## References

1. [Google Security Blog](https://security.googleblog.com/2017/02/announcing-first-sha1-collision.html) - Announcing the first SHA1 collision, 2017.
2. [Hash tables and amortized analysis](http://www.cs.cornell.edu/courses/cs312/2008sp/lectures/lec20.html) - CS 312 Lecture 20, Cornell, 2008.

[hash-table]: #hash-table
[linkedlist]: https://en.wikipedia.org/wiki/Linked_list
