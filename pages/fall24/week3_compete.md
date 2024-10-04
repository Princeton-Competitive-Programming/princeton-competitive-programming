---
permalink: /fall24/week3_compete
layout: page
---

{% include main_title.html text="Fall 24 - Compete Division Week 3" %}

Some hints for the problems:

* Problem A:
* Problem B:
* Problem C: observe that the optimal order is decreasing in ci/wi
* Problem D: there is a threshold c that we choose to refresh when the timer is larger than c
* Problem E: we only need to care for each vertex the first time some robot reaches it (modulo parity). Then it can be solved by shortest path.
* Problem F: to check if a face is shadowed you can check if the sun is "behind" the plane that the face lies in, and use the normal of the face defined by the points it contains and see the condition it must satisfy with a vector from the apex to the sun