---
permalink: /graph_s24
layout: page
---

{% include main_title.html text="Graph Search Algorithms" %}

If this is your first time at competitive programming, welcome! And
welcome back if you've been here before. The following problems are
all problems on graph search of increasing difficulty. The first two
are more direct applications of the depth-first search and
breadth-first search algorithms you know, with a small twist. The last
two problems are less direct and require a bit more creativity. Your
goal should be to solve at least one of the first two problems, but
the more problems you solve the more you'll get out of this.

I recommend you start by reading problem A and think about how you'd
go about solving it. If you are stuck or don't really know what to do,
start by reading the hints below. If you are still stuck ask for help!
Once you have an idea of what to do, try to implement a solution. Test
it with the sample test cases and try to submit (you can submit as
many times as you want). Once you get A accepted, progress to B, then
C and so on.

If you want a quick refresher on DFS and BFS, I recommend reading
chapter 12 of this [competitive programming
book](https://cses.fi/book/book.pdf). The example code is in C++, but
it should be easy to read if you know Java (the only thing you need to
know is that in C++ a vector is a resizing array, everything else is
self-explanatory).

## Hints for problem A. Cycle Detection

Start by creating an adjacency list and populate it with the edges
from the input. You don't have to create a whole graph or digraph
class from scratch (you can if you want to, but for this problem it's
overkill), but an array of
[ArrayLists](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)
should work.

Now you can use a DFS to detect cycles. Think about how to do it first
before looking for more hints.

The key idea is to add an additional `active[]` array that keeps track
of nodes whose exploration has begun but not finished. As we perform a
DFS, if we find an edge adjacent to an active node that indicates we
found a cycle.

## Hints for problem B. Escaping The Maze

This problem might not look to be a graph problem at first glance, but
there is an implicit unweighted graph represented by the grid, where
vertices are cells and edges are moves. You want to calculate a
shortest path in this graph, so you can use a BFS to do so. Now, there
are two possible approaches to this problem.

The first one is to convert this implicit graph in to an actual graph
(i.e. an adjacency list). We need to be a bit careful about the boost
move since we can only use it once, but one common trick we can apply
is having two copies of the graph representing the grid: one where we
haven't used the boost move and one where we have. In addition to the
normal edges, we can have edges from the first graph to the second
representing using the move.

The second one is to work with the implicit graph. We represent each
vertex as a triple: a column coordinate, a line coordinate and a bit
representing whether or not we've used the boost (which in the
previous example is like indicating which copy of the graph are we
in). Given a vertex (i.e. a column/line/bit triple), we can easily
determine what the adjacent vertices are. So we can use this to
perform a BFS without having to actually store adjacency lists.

Both options are perfectly fine, but it is recommended you try the
second one, because it is slightly more efficient and it's more
general (there are some problems where creating the explicit graph
from the implicit one isn't a good idea).

## Hints for problem C. New Year Transportation

Much like problem B, this problem presents us with an implicit
graph. Cells are vertices and edges are portals. We want to determine
if we can go from vertex 1 to vertex `t`, so this is a reachability
problem, which we can solve with a DFS or a BFS. A DFS is simpler to
implement, so we recommend using that option. Also, we again can
either create the explicit graph from the implicit, or just work with
the implicit one. The latter option is recommended.

## Hints for problem D. Fox And Names

This problem really doesn't look like a graph problem at all, but it
actually is! First, a lexicographical order of the letters is just
some permutation of the letters that induces a relative order between
them. We want to find one such that the words in the input are in
sorted order.

If a word `S` comes before a word `T`, then this means there is some
condition that the lexicographical order has to satisfy. Suppose the
first letter they differ one is a `c` for `S` and an `a` for `T`, for
example perhaps `S = abcmn` and `T = abaz`. Because `S` comes before
`T`, this means that `c` has to come before `a`. We can find all of
these dependencies by looking at all pairs of words.

How do we now find a lexicographical order? It's a topological order
on the graph induced by letters and dependencies on them! Build a
directed graph where vertices are letters and there is an edge between
two vertices v and u if v has to come before u. Determine if there are
cycles in the graph, if so then there are circular dependencies and
the answer is "impossible". Otherwise, find a topological order and
print the corresponding letters.