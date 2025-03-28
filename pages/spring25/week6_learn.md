---
permalink: /spring25/week6_learn
layout: page
---

{% include main_title.html text="Spring 25 - Learn Division Week 6" %}

Welcome to another week of competitive programming of Spring 2025!
Today's problem solving session will focus on **graphs and graph
search**.

But first, if this is your first time ever in one of our competitive
programming sessions, please see our [introduction guide]({{
site.baseurl }}/intro_guide) to get started. Once you're done, feel
free to come back here.

To make the most out of your experience in these sessions you should
read the introduction and then attempt to solve the problems one by
one, i.e. don't try working on B before solving A, C before solving A,
etc. You don't have to solve all the problems, you will be learning
something even if you only try to solve a single problem.

Feel free to work together with a friend or two, this is supposed to
be a collaborative environment. Also, if you are stuck or have
questions, don't keep them to yourself!  Talk to other people! If you
are not sure who to talk to, ask on discord.

Problem set [link]().

## Introduction

This week's problems are built around **graph traversal**, with
increasing difficulty. Here is a summary of some of the things you'll
need to know.

### Graph Representation

In Java, we typically represent graphs using adjacency lists. You
could create a whole graph or digraph object (like you might have seen
in COS226), but often you can get away by representing the adjacency
list as an array of
[`ArrayList`](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)
(which are like stacks implemented using resizable arrays).

```java
int n = 100005;
ArrayList<Integer>[] adj = new ArrayList[n];
for (int i = 0; i < n; i++) {
    adj[i] = new ArrayList<>();
}
adj[0].add(1); // add edge from 0 to 1
adj[1].add(2); // add edge from 1 to 2
```

The above is an **explicit representation** of a graph, where we store
nodes and edges directly. Sometimes it is useful to use an **implicit
representation**, where graph structure is hidden (usually a grid),
and we must infer edges. Working with an implicit representation is
often a way to simplify our implementation. We show an example of that
below.

### DFS

One of the main algorithms we use to traverse a graph is the
Depth-First Search (DFS), which is often useful for determining
reachability between vertices. Here is an example in Java.

```java
boolean[] visited = new boolean[n];

void dfs(int u) {
    visited[u] = true;
    for (int v : adj[u]) {
        if (!visited[v]) dfs(v);
    }
}
```

### BFS

Another important algorithm is the Breadth-First Search, which is
mainly useful because it lets us find the shortest paths between
vertices. Here is an example in Java.

```java
int[] dist = new int[n];
Arrays.fill(dist, -1); // -1 means unreachable
Queue<Integer> q = new LinkedList<>();

void bfs(int start) {
    q.add(start);
    dist[start] = 0;

    while (!q.isEmpty()) {
        int u = q.poll();
        for (int v : adj[u]) {
            if (dist[v] == -1) {
                dist[v] = dist[u] + 1;
                q.add(v);
            }
        }
    }
}
```

### BFS (implicit)

Here is an extra example that is given a `H` by `W` grid (named
`grid`) filled with either `.` or `#` and it determines shortest paths
that only use `.` cells (so it's like `.` are open cells and `#` are
obstacles, and this algorithm is finding paths in this map).

```java
int[][] dist;
int[] dx = {1, -1, 0, 0};
int[] dy = {0, 0, 1, -1};

void bfs(int sx, int sy) {
    dist = new int[H][W];
    for (int[] row : dist) Arrays.fill(row, -1);
    Queue<int[]> q = new LinkedList<>();
    q.add(new int[]{sx, sy});
    dist[sx][sy] = 0;

    while (!q.isEmpty()) {
        int[] cur = q.poll();
        int x = cur[0], y = cur[1];
        for (int d = 0; d < 4; d++) {
            int nx = x + dx[d];
            int ny = y + dy[d];
            if (0 <= nx && nx < H && 0 <= ny && ny < W) {
                if (grid[nx][ny] == '.' && dist[nx][ny] == -1) {
                    dist[nx][ny] = dist[x][y] + 1;
                    q.add(new int[]{nx, ny});
                }
            }
        }
    }
}
```

### Today's Problems

The following problems are all problems on graph search of increasing
difficulty. The first two are more direct applications of the
depth-first search and breadth-first search algorithms you know, with
a small twist. The last two problems are less direct and require a bit
more creativity. Your goal should be to solve at least one of the
first two problems, but the more problems you solve the more you'll
get out of this.

I recommend you start by reading problem A and think about how you'd
go about solving it. If you are stuck or don't really know what to do,
start by reading the hints below. If you are still stuck ask for help!
Once you have an idea of what to do, try to implement a solution. Test
it with the sample test cases and try to submit (you can submit as
many times as you want). Once you get A accepted, progress to B, then
C and so on.

### Extra Resources

If you want more information on DFS and BFS, I recommend reading
chapter 12 of this [competitive programming
book](https://cses.fi/book/book.pdf). The example code is in C++, but
it should be easy to read if you know Java (the only thing you need to
know is that in C++ a vector is a resizing array, everything else is
self-explanatory).

## Problem A. Cycle Detection

You can find the [problem description here](https://codeforces.com/group/hNnRWqFua0/contest/599534/problem/A). Read it and then come
back here.

You can use a DFS to detect cycles. Think about how to do it first
before looking for more hints.

The key idea is to add an additional `active[]` array that keeps track
of nodes whose exploration has begun but not finished. As we perform a
DFS, if we find an edge adjacent to an active node that indicates we
found a cycle.

## Problem B. Escaping The Maze

You can find the [problem description here](https://codeforces.com/group/hNnRWqFua0/contest/599534/problem/B). Read it and then come
back here.

This problem might not look to be a graph problem at first glance, but
there is an implicit unweighted graph represented by the grid, where
vertices are cells and edges are moves. You want to calculate a
shortest path in this graph, so you can use a BFS to do so. Now, there
are two possible approaches to this problem.

The first one is to convert this implicit graph in to an explicit
graph. We need to be a bit careful about the boost move since we can
only use it once, but one common trick we can apply is having two
copies of the graph representing the grid: one where we haven't used
the boost move and one where we have. In addition to the normal edges,
we can have edges from the first graph to the second representing
using the move.

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

## Problem C. New Year Transportation

You can find the [problem description here](https://codeforces.com/group/hNnRWqFua0/contest/599534/problem/C). Read it and then come
back here.

Much like problem B, this problem presents us with an implicit
graph. Cells are vertices and edges are portals. We want to determine
if we can go from vertex 1 to vertex `t`, so this is a reachability
problem, which we can solve with a DFS or a BFS. A DFS is simpler to
implement, so we recommend using that option. Also, we again can
either create the explicit graph from the implicit, or just work with
the implicit one. The latter option is recommended.

## Problem D. Fox And Names

You can find the [problem description here](https://codeforces.com/group/hNnRWqFua0/contest/599534/problem/D). Read it and then come
back here.

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