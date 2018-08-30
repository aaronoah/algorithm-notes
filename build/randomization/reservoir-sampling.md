# Reservoir Sampling

Labeled as _Algorithm R_ in the description by [Jeffrey Vitter](https://en.wikipedia.org/wiki/Jeffrey_Vitter) in his subject of [Random Sampling with a Reservoir](https://dl.acm.org/citation.cfm?id=3165), reservoir sampling is a common technique in data processing: randomly choose _k_ samples out of a set _S_ with n items wherein the n is either very large or unknown beforehand; all the chosen _k_ items form a "reservoir" in this sense and guarantee to have each of them chosen with equal probability 1/n.

## Formal Description

Given a stream of data of unknown size n, randomly select k items "reservoir" from it with equal probability by: saving the first k items in the array of size k. For each item j, wherein j>k, choose a random integer M from 1 to j, if M is smaller than k, then substitute the value of "reservoir" in index M with the value of array in index j.

_Note: assist in understanding the problem, there is an interesting post [here](https://www.quora.com/What-is-an-intuitive-explanation-of-reservoir-sampling) with an example of how girls fairly choose a date from a bunch of bachelors_.

## Algorithm R

```
ReservoirSample(S[1..n], R[1..k])
  // fill the reservoir array
  for i = 1 to k
      R[i] := S[i]

  // replace elements with gradually decreasing probability
  for j = k+1 to n
    M := random(1, j)   // important: inclusive range
    if M <= k
        R[M] := S[j]
```

This yields to &Omicron;(n) time in complexity.

To see how it works, consider a proof by induction:

After the (i-1)<sup>th</sup> round, let us assume, the probability of a number being in the "reservoir" is k / (i-1). Since the probability of the number being replaced in the i<sup>th</sup> round is 1 / i, the probability that it survives the i<sup>th</sup> round is (i-1) / i. Thus, the probability that a given number is in the "reservoir" after the i<sup>th</sup> round is the product of these two probabilities, i.e. the probability of being in the reservoir after the (i-1)<sup>th</sup> round, and surviving replacement in the i<sup>th</sup> round. This is (k / (i-1)) * ((i-1) / i) = k / i. Hence, the result holds for i, and is therefore true by induction.

## Additional References

1. Medium, Reservoir Sampling. https://medium.com/100-days-of-algorithms/day-33-reservoir-sampling-252062ce0baa
