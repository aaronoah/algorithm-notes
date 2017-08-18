# Discrete Probability

In the analysis of randomized algorithms, the concepts of [discrete probability][discrete-prob] help devise the mathematical models catering the needs to perform [asymptotic analysis](../asymptotic-analysis.md).

_Note: despite that continuous probability is also pivotal in various scientific worlds, [**discrete probability**][discrete-prob] is mostly used in the computing subjects and hence the major topic in this chapter._

The following definitions are essential to know for applications in randomized algorithm analysis.

## Indicator Random Variable

To analyze the various randomized algorithms, the definition of [Indicator Random Variable][indicator] is adopted:

<figure style="text-align:center">
  <img src="../images/indicator-random-variable.png" />
  <figcaption>Figure 1. Indicator Random Variable</figcaption>
</figure>

_Note: where &Alpha; denotes the [**event**][event] within the [sample space][sample space]_

## Conditional Probability

Given the sample space and its subsets event &Alpha;, &Beta;, etc. the [Conditional Probability](http://www.stat.yale.edu/Courses/1997-98/101/condprob.htm) denotes the concept that "event &Beta;'s probability to occur given the event &Alpha; happens as well":

&Rcy;(&Beta; | &Alpha;) = &Rcy;(&Alpha; &cap; &Beta;) / &Rcy;(&Alpha;)

<figure style="text-align:center">
  <img src="../images/event_a_b.jpg" />
  <figcaption>Figure 2. Venn Diagram of Intersection of Event &Alpha; and &Beta;</figcaption>
</figure>

if [event][event] &Alpha; and &Beta; are independent (_which means the events have no intersections graphically represented above._), &Rcy;(&Alpha; &cap; &Beta;) = &Rcy;(&Alpha;) &sdot; &Rcy;(&Beta;), &Rcy;(&Beta; | &Alpha;) = &Rcy;(&Beta;)

## Linearity of Expectation

Formal Def: let &Xscr;<sub>1</sub>, &Xscr;<sub>2</sub>, ..., &Xscr;<sub>n</sub> be random variables defined on [sample space][sample space]. Then:

<figure style="text-align:center">
  <img src="../images/linearity_of_exp.png" />
  <figcaption>Figure 3. Linearity of Expectation</figcaption>
</figure>

## Example Problems

To take advantage of the definitions above, there are several related probabilistic problems to cover.

### Birthday Paradox

How many people is needed at least in order that two of them having a 50-50 chance to born on the same day? The answer is an astonishing 23, which is far smaller than the total number of days in a year.

It is a _paradox_ given that only 70 people will have 99.9% possibility to discover two of them sharing the same birthday, much more efficient than finding such a pair in more than 366 people.

_**Proof**_:

Assume that leap year is not considered and all 365 days are equally likely to be chosen as one's birthday. (the differences of birth year is neglected)

To compute the probability of two people in a group sharing the same birthday, which can be seen as event A, a complementary event A' that no two individuals having the same birthday is introduced.

If a guy _a_ chooses day _d(a)_, then a guy _b_ must chooses day _d(b)_ &ne; _d(a)_ in order that event A' still holds. Then, a guy _c_ must not choose either of _d(a)_ or _d(b)_ as well.

By [conditional probability](#conditional-probability), _P(A')_ = 1 &sdot; (1 - 1/365) &sdot; (1 - 2/365) ... (1 - (n-1)/365), where _n_ is the total number of people.

According to [Taylor Series](https://en.wikipedia.org/wiki/Taylor_series) of the exponential function,

&iecy;<sup>x</sup> = 1 + x + x<sup>2</sup>/2! + .. &ap; 1 + x

Then, replace x with numbers in the _P(A')_ equation,

_P(A')_ = &iecy;<sup>-1/365</sup> &sdot; &iecy;<sup>-2/365</sup> .. &sdot; &iecy;<sup>-(n-1)/365</sup> = &iecy;<sup>-(n(n-1)/2)/365

_P(A)_ = 1 - _P(A')_ &ap; 1 - &iecy;<sup>-n<sup>2</sup>/2*365</sup>, and its curve shown below:

<figure style="text-align:center">
  <img src="../images/birthday_paradox.svg" />
  <figcaption>Figure 4. The computed probability of at least two sharing the same birthday against the total number of people</figcaption>
</figure>

Obviously, when the total number of people is 23, there is 50% chance to have at least two people ended up with same birthday; when it reaches 70, the probability is almost 100%. Then, proof ends.

[event]: https://www.mathsisfun.com/data/probability-events-types.html
[sample space]: https://en.wikipedia.org/wiki/Sample_space
[discrete-prob]: https://en.wikibooks.org/wiki/High_School_Mathematics_Extensions/Discrete_Probability
[indicator]: #indicator-random-variable
