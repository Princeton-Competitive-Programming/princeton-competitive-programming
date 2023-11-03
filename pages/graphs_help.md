---
permalink: /graphs_f23
layout: page
---

{% include main_title.html text="Greedy Algorithms" %}

## Hints for problem A. Biggest Island

This problem doesn't really seem to be about graphs, but it is about
an implicit graph: the grid graph. If you have never heard about
graphs, first read Chapter 11 of this
[book](https://cses.fi/book/book.pdf) (the code in the book is in C++,
but the only thing you need to know is that a vector in C++ is a like
an ArrayList in Java, so a resizing array).

So now you can consider each cell of the input as a vertex and each
one has an edge to the 4 adjacent cells. Note that you don't have to
create an actual graph and convert the input into a graph, you can
operate over the *implicit graph* representation of the grid. In other
words, if you need to, for example, go over the vertices adjacent to a
certain vertex, you can simply use a loop that changes the 2
coordinates to obtain each one of the top, bottom, left and right
cells.

So how should you approach calculating the biggest island area? The
biggest island is the size of the largest *connected component*, which
is a set of land blocks (vertices) that are connected (there is some
path between each pair of vertices). To compute such a thing you can
use a *Depth-First Search*, which you can read about in Chapter 12 of
the book (read only the first section, titled "Depth-first search".

So now the solution can be something like: run a DFS from each cell
and count how many cells you visited. Keep track of the maximum of
this and output that as the answer.

## Hints for problem B. Cycle Detection

Now we have an actual graph, so you have to create an adjacency list
and populate it with the edges from the input. Now you can use a DFS
to detect cycles. Think about how to do it first before looking for
more hints, but if you are stuck, Chapter 12 of the book has a section
called "Finding cycles" that explains how to do this.


## Hints for problem C. Transformation: from A to B

Again, this doesn't look like a graph problem, but it is! Think about
the numbers a and b as vertices, as well as any possible number you
can obtain from them. Edges represent transformations, e.g. 3 and 6
are adjacent because of the first transformation, 1 and 11 are
adjacent because of the second transformation. However, this is an
infinite graph, so you can really represent the whole thing, much like
problem A you want to represent it implicitly. Also notice that you
don't care about vertices of value larger than b, since those can
never have a path to b.

Now run a DFS from a and stop when you see b. You need to keep track
of the steps you are taking on your DFS, so you can output the path
you found (you can use a stack to do this, by inserting when you visit
a vertex and popping when just before returning from the dfs method
after processing the vertex).


## Hints for problem D. Rook, Bishop and King

This is another implicit graph problem where each cell is a vertex and
the edges are given by the rook, bishop or king moves. Now you want to
find the shortest path from a given cell to a different cell. You can
use a method called "Breadth-First Search" to do so, which you can
read about in Chapter 12 of the book (there is a section called
"Breadth-first search").