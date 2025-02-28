---
permalink: /spring25/week4_learn
layout: page
---

{% include main_title.html text="Spring 25 - Learn Division Week 4" %}

Welcome to another week of competitive programming of Spring 2025!
Today's problem solving session will focus on **sorting
algorithms**. You will be applying sorting algorithms to solve
problems.

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

## Problem A - Exam Room

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/592130/problem/A). Read
it and then come back here.

In this problem you'll have to apply sorting plus a simple
calculation. Read the problem now if you haven't already.

The size of the input $n$ can go up to $10^5$, so this means your
solution should work in $\Theta(n \log n)$ time or better.

The only trick you need to know is how to
sort. You shouldn't implement a sorting algorithm from scratch, use
the deafult sorting algorithm from your favorite programming
language. Here is a [link](https://usaco.guide/bronze/intro-sorting)
where you can learn about this (select your language at the top).

## Problem B - Pizza Line

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/592130/problem/B). Read
it and then come back here.

Once again, the size of the input $n$ can go up to $10^5$, so recall that this
means your solution should work in $\Theta(n \log n)$ time or better.

This problem is about computing something known as the number of
inversions of an array: the number of pairs $i, j$ such that $i < j$
but $p_i > p_j$. (Note that this exactly corresponds to the number of
comparisons made by a insertion sort algorithm). Computing this
directly looks hard (at least if you want to do it in time better than
$O(n^2)$). But there is a way of solving this problem based on
modifying merge sort. if you don't know how, think about it for a bit,
and then read the rest of this description.

Think about the following simplified problem: suppose you have an
array that is made of two sorted arrays (but the concatenation of the
two might not be sorted). How would you compute the number of
inversions of this array? Note that this is exactly the setup one
finds when using merge sort, specifically when merging two arrays. And
in fact you can modify the merge algorithm to count inversions. To
generalize this to any array, just use this modified
merge-inversion-count algorithm as a subroutine of merge sort.

## Problem C - Class Schedule

For this problem you will need to know about a technique called *sweep
line*. You can find information about this in [chapter 30 of the
Competitive Programmer’s
Handbook](https://usaco.guide/CPH.pdf#page=286) (you can skip sections
30.2 and 30.3 if you want, they are more advanced applications of the
technique that you don't need to know about quite yet). Once you read
this, read the [problem description here](https://codeforces.com/group/hNnRWqFua0/contest/592130/problem/C).

This problem is very similar to the first problem specified in the
above reading, but here you need to compute the length of the union of
all the intervals. The solution is very similar, so think about how
you can adapt the ideas from the reading to this problem.

## Problem D - Painting Fence

This next problem will graduate from sorting into a more general
technique known as "Divide and Conquer". This is the main concept that
we use in algorithms like merge sort: we divide the input into two
halves, solve/sort each one separately, and then merge/"conquer"
both. If you know how merge sort works you already know the intuition
behind this concept, so you don't need to do any background reading to
solve this problem. However, as you'll see shortly, it's not obvious
at all how to apply it here. Read the problem now.

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/592130/problem/D). Read
it and then come back here.

In this problem $n$ is at most $5000$, so a $O(n^2)$ solution is
enough to solve it. But there is a more efficient $\Theta(n \log n)$
solution. Before you read any of the following, think about the
problem on your own for a bit.

As you've probably guessed, the key idea you need is to use divide and
conquer, but how? First, observe that you can always paint the whole
fence with $n$ vertical strokes. Now, consider the lowest plank in the
fence, and suppose it is of height $x$. Any solution that doesn't use
all vertical strokes will have to use at least $x$ horizontal strokes,
since if you are going to use horizontal strokes, you might as well
cover the shortest planks first. If you add $x$ horizontal strokes,
now you can basically remove $x$ from the fence and it is now split
into two "subfences" (potentially of different sizes). How do you
handle the subfences? Well, note that it's the same problem that we
started with, but on a smaller input! So we just divided it. We'll
leave the rest of the solution up to you.