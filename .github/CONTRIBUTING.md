# Contributing to algorithm-cracker

When you find good materials to contribute to algorithm-cracker, we ask that you read our contributing guidelines carefully so that you spend less time struggling to push your PR through our code review processes.

At the same time, reading the contributing guidelines will give you a better idea of how to post meaningful issues that will be more easily be parsed, considered, and resolved. A big win for everyone involved! 🎉

## Table of Contents

* [How to use Git and Github](#how-to-use-git-and-github)
  * [Forking](#forking)
  * [Branching](#branching)
  * [Commits](#commits)
  * [Pull request](#pull-request)
  * [Code review](#code-review)
* [Code of Conduct](#code-of-conduct)

## How to use Git and Github

---

### Forking

We follow the [Github forking model](https://help.github.com/articles/fork-a-repo/) and any commits should follow by this pattern. Make sure you have a `upstream` which points to this repo.

### Branching

All work on the next major release goes into master, which means you should always make a `pull request` against the master branch.

### Commits

Feel free to make as many commits as you like. In your commit messages, please write helpful information on your changes, e.g. test: book generation with XXX; feat: add a new section on YYY, etc.

Resolve any merge conflicts if you happen to see one, when merging your PR, we will squash your commits into one commit.

### Pull request

Before you submit a pull request, make sure your branch is up-to-date and `rebase` any of your changes on the latest upstream branch.

```
git fetch upstream
git rebase upstream/master
```

### Code review

After submitting your pull request, we will take a look at what commits you want to merge into the master, make sure you follow your pull request thread closely and if things do not work out, we will let you know.

## Code of Conduct

Anything you contribute will be deemed as following the [MIT LICENSE](../LICENSE) and do read the license before you start contributing! If you submit your sophisticated algorithms that are under patent protection of any of such kind, we can not guarantee its safety!

Thank you so much for reading our guidelines! 🎉