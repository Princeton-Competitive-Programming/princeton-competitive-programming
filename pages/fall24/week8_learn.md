---
permalink: /fall24/week8_learn
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 8" %}

Welcome to the eight week of competitive programming of the Fall of
2024! Today's problem solving session will be about minimum spanning
trees and shortest paths. Read the introduction below before getting
started.

Before reading a problem, read its accompanying description available
below. Work through the problems one by one, i.e. don't try working on
B before solving A, C before solving A, etc.

But first, if this is your first time ever in one of our
competitive programming sessions, please follow the instruction on our
new [introduction guide]({{ site.baseurl }}/intro_guide) to get
started. Once you're done, feel free to come back here.

Problem set [link](https://codeforces.com/group/hNnRWqFua0/contest/565211).

## Introduction

Today's session is about the minimum spanning trees and shortest
paths. The first 2 problems are mostly about implementing the two main
algorithms in this theme, and the last 2 are slightly more involved
applications of these algorithms to some problems. In the first one
your pretty much only have to implement a minimum spanning tree
algorithm (either Kruskal's or Prim's) and in the second one you have
to implement Dijsktra's algorithm. The last two problems are a bit
tricky, but we have some hints below to help you.

If you want a quick refresher, I recommend reading chapter 14 for MST
algorithms and 13.2 for Dijsktra's of this [competitive programming
book](https://cses.fi/book/book.pdf). The example code is in C++, but
it should be easy to read if you know Java.

## [Problem A. Princeton Paths](https://codeforces.com/group/hNnRWqFua0/contest/565211/problem/A)

So this isn't a direct MST problem, but the only trick you can use is
that you want an MST over the graph where the edges not under
construction are free (i.e. have weight 0).

## [Problem B. Dijkstra](https://codeforces.com/group/hNnRWqFua0/contest/565211/problem/B)

Implementing Dijkstra's isn't very hard, but it is surprisingly very
easy to write buggy code that is slower than expected or just plain
incorrect. For example, right after popping a node from the priority
queue, make sure you check if that node hasn't been processed before
processing it again. Also, note that you have to reconstruct the
graph, so you need to keep track of an `edgeTo[]` array.

## [Problem C. Inverse the Problem](https://codeforces.com/group/hNnRWqFua0/contest/565211/problem/C)

At first this problem seems like it's about shortest paths, but to
solve it you have to think about MSTs! Your solution should try to
build the original tree from the distance matrix, and then build the
distance matrix from that tree and verify that the two are
consistent. Note that you can calculate distances in trees using a DFS
algorithm (i.e. you don't need to implement a fancier algorithm like
Dijkstra's), since there is only one path between any two nodes (so a
DFS will find this one path).

(if you are stuck for a while ask for help!)

## [Problem D. Bicycles](https://codeforces.com/group/hNnRWqFua0/contest/565211/problem/D)

It might be tempting to try to modify Dijkstra's algorithm, but this
is actually not the best strategy. Like a lot of problems related to
shortest paths, you actually want to build a new graph where the
shortest path on this graph is the solution to the original problem.

Suppose you try to do the following: build a graph with $1000n$ nodes,
where each node is corresponds to a pair $(i, s)$, where $i$ is a city
index and $s$ is the speed we have when we are at this city. Can you
come up with a way of placing edges between these vertices such that
the shortest path from $(1, s_1)$ to some $(n, j)$ corresponds to the
solution to the original problem? Once you do, just run Dijkstra's on
this new graph.