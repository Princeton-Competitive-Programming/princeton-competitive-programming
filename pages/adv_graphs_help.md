---
permalink: /adv_graphs_s24
layout: page
---

{% include main_title.html text="Graph Problems" %}

## Hints for problem A. Judging Gifts

Start by creating a graph of gift exchanges. Now, if there is a cycle
that contains y, the answer is always yes, since you could have traded
an arbitrary amount of times. Otherwise, the graph forms a DAG (at
least the part reachable from y), so now we want to compute the
longest path from y to any other node in a DAG and check whether it is
greater than k. This is a classic problem you can solve with dynamic
programming.

## Hints for problem B. Brexit Negotiations

Here is a way of summarizing the problem: Given a DAG with vertex
weights e(i), find a topological ordering p that minimizes: max_i
{e(p(i)) + i}.

This problem is ultimately about topological sorting, but one that
minimizing the above formula. Think about how the algorithm to find a
topological sort works (i.e. find a node with no outdegree, remove and
repeat) and whenever you have multiple choices make a greedy choice
(i.e. the one that minimizes the above formula). You might need to use
an extra data structure to help you make the greedy choice, but in the
end the algorithm will look very similar to a topological sort
algorithm.

## Hints for problem C. Locking Doors

The problem looks hard, but there is a simple answer. Think about
strongly connected components (if you don't know what this is, read
[chapter 17 of this book](https://cses.fi/book/book.pdf)). In a
strongly connected component you can get everywhere without having to
add new exits, but once you close all the doors in that component you
have to move on to a different strongly connected component or you are
stuck. So the answer is the number of strongly connected components
with not outgoing edges.

## Hints for problem D. Perpetuum Mobile

The problem asks to find a cycle where the product of the weights is
at least 1. It almost sounds impossible (since it looks like a longest
cycle problem), but there is a trick that makes this problem much
easier. Take the logarithm of each weight, now the problem is
equivalent to finding a cycle whose sum of weights is positive. To
solve this problem, negate all of the weights and then find a negative
cycle by using Bellman-Ford.

## Hints for problem E. International Irregularities

Observation: you jump at most once, and only in the very beginning. So
know there are 5 cases to analyze: hop directly if possible; hop to
the right up to m at a time; jump directly to y; jump right of y, then
hop left once; jump left of y, then hop right some times. Each one of
these can be computed in O(log n) or O(1) time by doing some
precomputation.