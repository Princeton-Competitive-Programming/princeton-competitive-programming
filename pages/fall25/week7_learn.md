---
permalink: /fall25/week7_learn
layout: page
---

{% include main_title.html text="Fall 25 - Learn Division Week 7" %}

Welcome to another week of competitive programming of Fall 2025! Today's
problem-solving session will focus on **dynamic programming**.

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

## Introduction

Dynamic programming is a very popular problem-solving technique that decomposes
a problem into subproblems and them tries to avoid recomputing the solution to
the same subproblem twice. It's very hard to learn dynamic programming
generically, it's a concept you learn by looking at many problems, and then you
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

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/650960/problem/A).

## Problem B. Cheesiest Slice

Read the second section of chapter 7 of the book. You can find the [problem
description
here](https://codeforces.com/group/hNnRWqFua0/contest/650960/problem/B).

## Problem C. Cheesiest Slice II

Read the second section of chapter 7 of the book. You can find the [problem
description here](https://codeforces.com/group/hNnRWqFua0/contest/650960/problem/C).

## Problem D. Boredom

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/650960/problem/D). Read it
and then come back here.

First note that it doesn't matter which element is which, we only need
to know how many 1s, 2s, ... are there. So start by collecting them in
some new array `c`, where `c[i] = #j such that a[j] = i`. Now the
point is that for each number we can either take it or we can take the
adjacent ones. Can you use this to come up with a recurrence? Once you
have it, the solution should be easy.