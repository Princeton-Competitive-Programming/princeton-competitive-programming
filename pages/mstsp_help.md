---
permalink: /mstsp_s24
layout: page
---

{% include main_title.html text="MST and Shortest Path Algorithms" %}

Today's session is about the minimum spanning trees and shortest
paths. Usually we have 3 or 4 problems, but today we have only 2. In
the first one your pretty much only have to implement a minimum
spanning tree and in the second one you have to implement Dijsktra's
algorithm.

If you want a quick refresher, I recommend reading chapter 14 for MST
algorithms and 13.2 for Dijsktra's of this [competitive programming
book](https://cses.fi/book/book.pdf). The example code is in C++, but
it should be easy to read if you know Java.

## Hints for problem A. Princeton Paths

So this isn't a direct MST problem, but the only trick you can use is
that you want an MST over the graph where the edges not under
construction are free (i.e. have weight 0).

## Hints for problem B. Dijsktra's

No hints, it's just "implement Dijsktra's".