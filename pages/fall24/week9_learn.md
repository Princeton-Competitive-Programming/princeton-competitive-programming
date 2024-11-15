---
permalink: /fall24/week9_learn
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 9" %}

Welcome to the ninth week of competitive programming of the Fall of
2024! Today's problem solving session will be about *dynamic
programming*! Read the introduction below before getting started.

Before reading a problem, read its accompanying description available
below. Work through the problems one by one, i.e. don't try working on
B before solving A, C before solving A, etc.

But first, if this is your first time ever in one of our
competitive programming sessions, please follow the instruction on our
new [introduction guide]({{ site.baseurl }}/intro_guide) to get
started. Once you're done, feel free to come back here.

Problem set [link](https://codeforces.com/group/hNnRWqFua0/contest/566988).

## Introduction

Dynamic programming is a very popular problem solving technique that
in its essence tries decompose a problem into subproblems and them
tries to avoid recomputing the solution to the same subproblem
twice. It's very hard to learn dynamic programming generically, it's a
concept you learn by looking at many many problems and then you
eventually start noticing similar patterns in new problems.

To get started learning about this, read Chapter 7 of this
[book](https://cses.fi/book/book.pdf). It contains a brief description
of the technique followed by lots of examples. You don't have to
understand all the examples to be able to solve the problems from
today's problem, set, once you understand the first example I
recommend trying to solve the first two problems (the second example
of the book is exactly the second and third problems of this problem
set).

## Problem A. Fibonacci

This is the simplest most common example of dynamic programming out
there. There is no trick here, just implement the formula from the
problem statement in a non-recursive way (or in a recursive way with
memoization). If you are having trouble with the modular operator, ask
for help (during the event or on discord).

## Problem B. Cheesiest Slice

Read the second section of chapter 7 of the book.

## Problem C. Cheesiest Slice II

Read the second section of chapter 7 of the book.

## Problem D. Boredom

First note that it doesn't matter which element is which, we only need
to know how many 1s, 2s, ... are there. So start by collecting them in
some new array `c`, where `c[i] = #j such that a[j] = i`. Now the
point is that for each number we can either take it or we can take the
adjacent ones. Can you use this to come up with a recurrence? Once you
have it, the solution should be easy.