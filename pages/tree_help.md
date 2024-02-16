---
permalink: /trees_s24
layout: page
---

{% include main_title.html text="Trees" %}

The problems from this week are pretty challenging. If you are feeling
stuck on a problem ask for a hint or for help.

## Hints for problem A. Valera and Elections

First observation: if an problem road is in a path of a different
problem road to 1, then it won't be considered.

Root the tree on vertex 1 and come up with a dynamic programming
solution to find how many nodes have some problem road on their
subtree. Then add all the problem roads that have no problem roads on
their subtree.

## Hints for problem B. Tree Tag

There are a few cases to consider depending on the relative value of
da to db. Analyze them to come up with the answer. There is one tricky
case, which is when 2da is greater than or equal to the diameter of
the tree. If you don't know what this is or how to efficiently compute
it, read [Chapter 14.2 of the Competitive Programmer’s
Handbook](https://cses.fi/book/book.pdf).

## Hints for problem C. Minimum spanning tree for each edge

The problem looks very hard at a glance, but the idea is to use the
following observation: suppose M is the MST of the graph. If (u, v) is
an edge in M, then the answer for this edge is the weight of
M. Otherwise, the answer is MST minus the heaviest edge in the path
from u to v in the MST, plus the weight of (u, v). To efficiently find
the heaviest edge in the path from u to v in the MST you can use a LCA
(lowest common ancestor) algorithm (modified to include maximum
weights). If you have never heard of this concept, read the
[cp-algorithms article on binary
lifting](https://cp-algorithms.com/graph/lca_binary_lifting.html).

## Hints for problem D. LCA Counting

Two observations:

 - The answer for k is at most 2k-1
 - For a given k, color all the vertices in the given set, then if
there are colored vertices in the subtree of u, then u has at most 2
children whose subtrees contain colored vertices

Use this observation to come up with a dp algorithm to compute which
nodes will be "repeats" of the 2k-1 upperbound.

## Hints for problem E. 0 Tree

Good luck :)