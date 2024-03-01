---
permalink: /greedy_s24
layout: page
---

{% include main_title.html text="Greedy Algorithms" %}

This week's problems are on "Greedy Algorithms". This is a class of
algorithms that construct solutions by always making a choice that
looks locally best, i.e. the best at the moment. Most problems do not
admit greedy solutions since often the local choice isn't the global
choice (think about minimizing a function with two minima, a local
minimum might not be a global minimum), but there are a few problems
where the right observations lead to a greedy algorithm that is
actually correct (think about minimizing a convex function with a
single minimum).

It's very hard to learn how to find greedy solutions to problems that
admit them generically, it's a concept you learn by looking at many
many problems and then you eventually start noticing similar patterns
in new problems.

To get started learning about this, read Chapter 6 of this
[book](https://cses.fi/book/book.pdf). It contains a brief description
of the technique followed by lots of examples. You don't have to
understand all the examples to be able to solve the problems from
today's problem set. In particular, feel free to ignore the last two
section on data compression and Huffman coding.

## Hints for problem A. Delivery Forces

First think if the largest element can be a median. It's easy to see
that that's not possible. What about the second largest element? It
can be a median if it is in the same group as the largest element, so
let's put those to elements together. What other element should we
pick to use in this group? Whatever we pick will be ignored (since it
isn't a median) so might as well choose the smallest one.

Can you now turn this intuition into a full algorithm by always being
greedy about what elements you pick?

## Hints for problem B. Valera and Fruits

The greedy decision you should make is to collect as many fruits as
possible. But in any given day some of the fruit might be good for one
more day and some might wither in the same day. So it's probably
better to take the ones that are going to wither sooner.

Convince yourself that this intuition always leads to an optimal
decision and then then convert it into an algorithm.

## Hints for problem C. Tea Party

"Every cup will contain tea for at least half of its volume", this
condition is hard so try to minimally satisfy it first (so fill up
every cup with the minimal amount of tea possible to satisfy it). If
you can, now if you fill up the largest cup with the remaining tea,
does anyone get unsatisfied? If you have tea left, if you fill up the
second largest cup, does anyone get unsatisfied?

## Hints for problem D. Heidi and Library

The key thing in this problem is deciding how to solve the following
situation: there are k books in the library and we need to discard one
to replace it with a new one, which book should we discard? If there
is a book you won't need anymore in the future (by looking at the
future requests), might as well get rid of that. If there is no such
book, what about the book you won't need for the longest time?

## Hints for problem E. Most socially-distanced subsequence

Think about the simpler case when the sequence is increasing or always
decreasing. What would the solution be in that case? Once you solve
this simpler case, what if the solution is always increasing, except
for one index of the array? If you solve these two cases you should be
able to generalize it to a solution for all possible sequences.