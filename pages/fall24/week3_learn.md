---
permalink: /fall24/week3_learn
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 3" %}

Welcome to the third week of competitive programming of the Fall of
2024! Today's problem solving session will be about the concept of
binary search. You probably know about binary search as a way to find
elements in an array, but we will use this concept in a more general
way today.

Before reading a problem, read its accompanying description available
below. Work through the problems one by one, i.e. don't try working on
B before solving A, C before solving A, etc.

But first, if this is your first time ever in one of our
competitive programming sessions, please follow the instruction on our
new [introduction guide]({{ site.baseurl }}/intro_guide) to get
started. Once you're done, feel free to come back here.

Problem set [link](https://codeforces.com/group/hNnRWqFua0/contest/553384).

## Problem A - [Parity Sort](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/A)

This first problem is a warm up problem that isn't really about binary
searching. As you know, in order to binary search over something, we
need that something to be sorted, so this first problem is about
sorting. Read the problem if you haven't already.

Given the constraint on $n$, you need a solution that runs in
$\Theta(n \log n)$ or better. If you aren't quite sure how to solve
it, here is a hint. Note that after doing any number of operations,
all the indices containing odd numbers still contain odd numbers and
all indices containing even numbers also contain even numbers. This
observation should tell you something about whether you can do it or
not (look at the sorted array and see if it satisfies it).

## Problem B - [Course Selection](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/B)

Read the problem now if you haven't already. Given the constraints,
you need to solve this in time $\Theta(N \log Q)$ or $\Theta(Q \log
N)$ or better.

This is a typical binary search problem. If you need a reminder on
binary search, read the section on binary search of this
[book](https://cses.fi/book/book.pdf#section.3.3).

If you still need some extra help, here is a hint. The problem
requires efficiently determining the existence of courses with
specific course numbers within a sorted list of course numbers. After
reading the input data, use binary search to check if a query course
number exists in the list.

## Problem C - [Dining Halls](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/C)

This problem is the first one where you won't use binary search on an
array. This problem requires a technique known as "binary search the
answer", which is a very powerful and useful technique you will need
for this and the remaining problems. First, read chapter 12 of these
[notes](https://darrenyao.com/usacobook/java.pdf#page=68).

Read the problem now if you haven't. Given the constraint on $n$ and
$t$, you need a solution that runs in $\Theta(n \log t)$ or
better. The idea you need here is similar to the example from the
reading. To apply the binary search the answer technique here we need
two things:

* Turn the problem into a decision problem (i.e. `check` method like
in the first pseudocode example from the reading). In this case it
should be something like: given a possible answer $k$, can we
determine whether the $n$ cooks can make $t$ meals in $k$ time?
* We need the answer to be monotone (i.e. either increasing or
decreasing). In this case, if the $n$ cooks can make $t$ meals in $k$
time, then can definitely make $t$ meals in $k'$ time if $k' \geq
k$. Conversely, if the $n$ cooks can't make $t$ meals in $k$ time,
then can't make $t$ meals in $k'$ time if $k' \leq k$.

So now all you need to solve this problem is implement the `check`
method and determine appropriate upper and lower bounds for the any
possible answer. With the latter, be careful with overflows (the
answer might not fit in an integer)!

## Problem D - [Kayaking Trip](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/D)

Read the problem. Given the constraints on $b+n+e$, you need a solution
that runs in $\Theta((b+n+e) \log (b + n + e))$ or better

Again the trick here is to binary search over the answer (i.e. the
maximum speed of the slowest kayak). This problem is certainly more
complex than the previous one, but you can solve it by applying the
same recipe: define a `check` function and make sure it is
monotone. The natural `check` function is: given a speed $v$, can we
distribute the participants such that the slowest kayak has speed at
least $v$? It's clear that this is monotone.

Now we reduced this problem to solving the `check` method, but this
isn't as easy as in the previous problem! Think about it for a while,
if you need a hint, keep reading.

Recall that the problem we are trying to solve is the following: given
a speed of $v$, can we assign people to kayaks such that each has
speed at least $v$? Think greedily. Take the kayak with lowest $c$. It
will have to be assigned two people, so give it the two people with
lowest strengths such that the resulting velocity is at least
$v$. Think about why this works, it's not obvious.

## Problem E - [The Meeting Place Cannot Be Changed](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/E)

Read the problem. Given the constraint on $n$, you need a solution
that runs in $\Theta(n \log (\max x + \max v))$ or better

Same goal as before, so you know the gist. There is one difference
here, which is that the answer isn't necessarily an integer, but the
idea is the same. Keep reading for a hint.

Let's try to check if it is possible to meet within $t$ seconds. In
this time, the $i$th friend can get anywhere within the segment
$[x_i - t\cdot v_i, x_i + t \cdot v_i]$. For the meeting to be
possible, there must be a point common to all these segments, that is,
their intersection must be non-empty. We can do this in linear time
(it's very similar to the Class Schedule problem from last week!). If
we verify that the friends can me within $t$ seconds, then they
definitely can meet within $> t$ seconds, if they can’t meet within
$t$ seconds then they can’t meet within $< t$ seconds. We can use this
intuition to implement our binary search.

