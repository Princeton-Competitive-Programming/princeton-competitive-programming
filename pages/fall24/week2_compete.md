---
permalink: /fall24/week2_compete
layout: page
---

{% include main_title.html text="Fall 24 - Compete Division Week 2" %}

Some hints for the problems:

* Problem A: What defines the boundaries of a rectangle? How many ways are there of defining these?
* Problem B: Use dynamic programming on segments.
* Problem C: What is the expected location after one day? What about after 2? And 3?
* Problem D: You should consider 3 cases: when the max and min differ by more than one, when max and min differ by exactly 1, and when max and min are the same.
* Problem E: One approach is to use range query data structures plus some simple observations, but there is a simpler (and nicer) solution based on divide and conquer.
* Problem F: Use a variant of the Euler-tour tree, where we do "BFS-children-first-DFS".