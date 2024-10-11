---
permalink: /fall24/week4_learn
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 4" %}

Welcome to the fourth week of competitive programming of the Fall of
2024! Today's problem solving session will be about data
structures. Read the introduction below before getting started.

Before reading a problem, read its accompanying description available
below. Work through the problems one by one, i.e. don't try working on
B before solving A, C before solving A, etc.

But first, if this is your first time ever in one of our
competitive programming sessions, please follow the instruction on our
new [introduction guide]({{ site.baseurl }}/intro_guide) to get
started. Once you're done, feel free to come back here.

Problem set [link](https://codeforces.com/group/hNnRWqFua0/contest/555432).

## Introduction

These week's problems are all about fundamental data structures. You
shouldn't have to implement any new data structure, but rather use the
built-in ones that come with your favorite programming language. If
you don't know how to use a symbol table/binary search tree, a stack
or a queue, spend some time researching your programming language's
built-in versions of these.

## Problem A. New Netids

This problem is supposed to be an straightforward application of a
symbol table data structure. Regardless of what language you are using
there is probably a data structure in its standard library (probably
called something close to *set*, e.g. in Java it's a
[TreeSet](https://docs.oracle.com/javase/8/docs/api/?java/util/TreeSet.html))
that supports inserting and checking if an element is in it. To solve
this problem you should learn how to use it and then apply it.

## Problem B. Word Game

This is also supposed to be a straightforward application of a data
structure, but of a map/dictionary/symbol table. First insert the
input into the data structure using the words as keys and the values
as a count of their frequency, and then go through the input again to
tally up the points. To solve this problem you should learn how to use
the default map/dictionary/symbol table data structure from your
favorite programming language and then use it.

## Problem C. Restoring the Duration of Tasks 

Another problem for you to learn how to use a data structure: a
queue. To solve it you have to simulate this process, by keeping track
of the current time:

* Take a task from the queue
* Take as time the maximum from the current time and from the arrival time of the task
* Subtract the current time from the time when the task was done
* Replace the current time with the time the task was done
* If there is a task in the queue, go to item 1

## Problem D. Social Network

This problem is an implementation problem, you don't need to think too
much about it. You have to implement a data structure that looks like
a stack (so you can see the most recent conversation on the screen and
add new conversations if there are less than $k$), but where you have
arbitrary access to any element (so you can swap and shift).

## Problem E. Greg and Array

This is the most challenging problem and uses a technique that is not
usually very well-known called *difference arrays*. Make sure you
know how it works first ([here is an article about
it](https://codeforces.com/blog/entry/78762)). Then to apply it to
this problem you have to do it twice, once to each of the m
operations, and then you have to use a "difference array of difference
arrays" approach to apply each one of the $k$ queries. It's a bit
tricky, but it's very worth it once you solve it.