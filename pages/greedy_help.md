---
permalink: /greedy_f23
layout: page
---

{% include main_title.html text="Greedy Algorithms" %}

## Hints for problem A. The number on the board

If you have to replace a digit with a different digit, might as well
set it to the largest possible digit (9), since that increases the sum
as much as possible. You if you have to pick a digit to replace, might
as well replace the smallest digit first, since that will increase the
sum by the most possible.

## Hints for problem B. Tea Party

"Every cup will contain tea for at least half of its volume", this
condition is hard so try to minimally satisfy it first (so fill up
every cup with the minimal amount of tea possible to satisfy it). If
you can, now if you fill up the largest cup with the remaining tea,
does anyone get unsatisfied? If you have tea left, if you fill up the
second largest cup, does anyone get unsatisfied?

## Hints for problem C. Heidi and Library

The key thing in this problem is deciding how to solve the following
situation: there are k books in the library and we need to discard one
to replace it with a new one, which book should we discard? If there
is a book you won't need anymore in the future (by looking at the
future requests), might as well get rid of that. If there is no such
book, what about the book you won't need for the longest time?

## Hints for problem D. Most socially-distanced subsequence

Think about the simpler case when the sequence is increasing or always
decreasing. What would the solution be in that case? Once you solve
this simpler case, what if the solution is always increasing, except
for one index of the array? If you solve these two cases you should be
able to generalize it to a solution for all possible sequences.