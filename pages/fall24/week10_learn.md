---
permalink: /fall24/week10_learn
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 10" %}

Welcome to the tenth week of competitive programming of the Fall of
2024! Today's problem solving session will be about *greedy
algorithms*! Read the introduction below before getting started.

Before reading a problem, read its accompanying description available
below. Work through the problems one by one, i.e. don't try working on
B before solving A, C before solving A, etc.

But first, if this is your first time ever in one of our
competitive programming sessions, please follow the instruction on our
new [introduction guide]({{ site.baseurl }}/intro_guide) to get
started. Once you're done, feel free to come back here.

Problem set [link](https://codeforces.com/group/hNnRWqFua0/contest/568633).

## Introduction

Much like dynamic programming, this week's topic isn't a specific
algorithm, but a paradigm that can be applied to some problems. The
key idea is the following heuristic approach: make the locally optimal
choice at each step with the hope of finding a global
optimum. Obviously this doesn't work for all sorts of problems, but
when it does the algorithm is often quite simple. So the science
(art?) of solving a problem using a greedy method is in identifying
that the problem is solvable by a greedy method. This is really hard
to do in general, the only way to do that is by seeing lots of
problems and noticing different patterns, so that's what you'll do
today. All the problems from today's session are solvable by a greedy
algorithm. Spend some time thinking about it and look at the hints if
you are stuck. Also, you might want to read chapter 6 of this
[book](https://cses.fi/book/book.pdf) for an introduction to some
well-known examples of problems with greedy solutions.

## Problem A. The number on the board

If you have to replace a digit with a different digit, might as well
set it to the largest possible digit (9), since that increases the sum
as much as possible. You if you have to pick a digit to replace, might
as well replace the smallest digit first, since that will increase the
sum by the most possible.

## Problem B. Tea Party

"Every cup will contain tea for at least half of its volume", this
condition is hard so try to minimally satisfy it first (so fill up
every cup with the minimal amount of tea possible to satisfy it). If
you can, now if you fill up the largest cup with the remaining tea,
does anyone get unsatisfied? If you have tea left, if you fill up the
second largest cup, does anyone get unsatisfied?

## Problem C. Heidi and Library

The key thing in this problem is deciding how to solve the following
situation: there are k books in the library and we need to discard one
to replace it with a new one, which book should we discard? If there
is a book you won't need anymore in the future (by looking at the
future requests), might as well get rid of that. If there is no such
book, what about the book you won't need for the longest time?

## Problem D. Most socially-distanced subsequence

Think about the simpler case when the sequence is increasing or always
decreasing. What would the solution be in that case? Once you solve
this simpler case, what if the solution is always increasing, except
for one index of the array? If you solve these two cases you should be
able to generalize it to a solution for all possible sequences.