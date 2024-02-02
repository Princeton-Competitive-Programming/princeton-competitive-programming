---
permalink: /dp_s24
layout: page
---

{% include main_title.html text="Dynamic Programming" %}

This problem set assumes you already know the basics of dynamic
programming and have some experience solving the classics.

Dynamic programming is a technique that you can only learn by doing
lots of examples, so this problem sets contains problems each of which
needs a different kind of observation.

## Hints for problem A. Pie Rules

This is a warm-up problem that is a direct application of dynamic
programming. Note that it doesn't mean the problem is trivial, it is
certainly different from the classics you might have seen before, so
you might have to think about it for a second if you haven't solved a
dynamic programming problem in a while.

Define the value of the game at each position, given the
current player, and then write down the possible transitions. Once you
do, the implementation should be obvious.

## Hints for problem B. Island Tour

The obvious solution that tries all possible starting attractions and
then simulates is too slow (O(n^4) runtime). You need something O(n^3)
or better. Think about ways of precomputing something that will help
you simulate more efficiently. Continue reading for a mild spoiler.

To solve this problem you have to make the observation that you can
decouple the trio into three pairs, and thus precompute pairwise
validity in O(n^3) time and use that to simulate all starting
attractions.

## Hints for problem C. Great Expectations

This problem seems like a not super hard direct application of dynamic
programming until you realize that you don't know how to compute the
base case (since the base case is what you want).

The trick to getting over this is that you can guess the answer, and
then use the DP solution to check if you guessed correctly. Combine
this with binary search and you'll find the right answer
eventually. (This problem has an interesting Markov Chain property and
basically what it is asking you is to find a stationary value of a
dynamic process. You don't need to know this to solve the problem, but
it's an interesting fact)

## Hints for problem D. Pillars

It's not hard to write a dynamic programming formulation of this
problem that can be implemented in O(n^2) time. You might be tempted
to make observations and try to simplify this formulation, but you
don't have to. Note that even though the naive implementation of this
DP is quadratic, you can implement it in O(nlog n) time if you use the
right data structure. Notice how knowing the maximum over prefixes
might help you do so.

## Hints for problem E. Random Tree Parking

This problem requires a lot of observations and clever thinking. If
you are stuck here is a observation that might help:

Given any tree T with n vertices and a sequence s, s is a parking
function of T if and only if for all vertices v in T, the number of
values i such that s(i) is in the subtree of v is larger than the
number of vertices in the subtree of v.

(Thinking about how to prove this claim might also give you some
insights on how to use it)

Converting this into a DP solution is still not obvious. Try to come
up with a O(n^3) solution first, and then think about how to optimize
it.

You'll also need to use the fact that because the trees are random,
their height will be logarithmic with high probability.