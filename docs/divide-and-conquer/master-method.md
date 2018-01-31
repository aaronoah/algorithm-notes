# Master Method

[DnC](overview.md) always involve a general pattern as it is defined in overview section. By defining such recurrence relations in a strong mathematical interpretation, as the [Master Method](#master-method), we can eliminate the duplication of solving new DnC instances.

## Theorem

* Things to know:

  1. branching factor a: number of sub-problems branching from one.
  2. recursion tree depth k = log<sub>b</sub>n.
  3. size of a sub-problem: n/b<sup>k</sup>.

  define a typical DnC complexity by:
  &Tau;(n) = a&Tau;(n/b) + &Omicron;(n<sup>d</sup>)
  for a > 0, b > 1, d &ges; 0
<figure style="text-align:center">
  <img src="../images/master-method.png" />
  <figcaption>Figure 1. Problem of size n is divided into a sub-problems of size n/b</figcaption>
</figure>

With that in mind, we formulate a theorem:
<figure style="text-align:center">
  <img src="../images/master-method-f.jpg" />
  <figcaption>Figure 2. Master Method Theorem</figcaption>
</figure>

_**Proof**_: Evaluate the complexity of DnC problem at level k would yield:

a<sup>k</sup> number of sub-problems, and each of size n/b<sup>k</sup>, therefore, the asymptotic complexity in the _k_ th level would be:

a<sup>k</sup> &sdot; &Omicron;(n/b<sup>k</sup>)<sup>d</sup> =
&Omicron;(n<sup>d</sup>) &sdot; (a/b<sup>d</sup>)<sup>k</sup>,
k = 0, 1, ...log<sub>b</sub>n

Recall from the [Geometric Series Sum](https://en.wikipedia.org/wiki/Geometric_series):

1 + &rfr; + &rfr;<sup>2</sup> + ... + &rfr;<sup>n</sup> = (&rfr;<sup>k+1</sup> - 1) / &rfr; - 1

Combining the k series:

&Tau;(n) = (log<sub>b</sub>n + 1) &sdot; &Omicron;(n<sup>d</sup>) &sdot; (1 + (a/b<sup>d</sup>) + (a/b<sup>d</sup>)<sup>2</sup> + ..+(a/b<sup>d</sup>)<sup>log<sub>b</sub>n</sup>),

&Tau;(n) = &scy; &sdot; &Omicron;(n<sup>d</sup>) &sdot; ((a/b<sup>d</sup>)<sup>log<sub>b</sub>n + 1</sup> - 1) / ((a/b<sup>d</sup>) - 1)

* a/b<sup>d</sup> = 1, &Tau;(n) = &Omicron;(n<sup>d</sup> &sdot; log(n))
* a < b<sup>d</sup>, &Tau;(n) &les; &Omicron;(n<sup>d</sup>) &sdot; (1 / 1- (a/b<sup>d</sup>)), &Tau;(n) = &Omicron;(n<sup>d</sup>)
* a > b<sup>d</sup>, &Tau;(n) &ap; &Omicron;(n<sup>d</sup> &sdot; (a/b<sup>d</sup>)<sup>log<sub>b</sub>n</sup>) = &Omicron;(n<sup>d</sup> &sdot; b<sup>-d &sdot; log<sub>b</sub>n</sup> &sdot; a<sup>log<sub>b</sub>n</sup>) = &Omicron;(a<sup>log<sub>b</sub>n</sup>) = &Omicron;(n<sup>log<sub>b</sub>a</sup>)

The theorem holds, proof ends.