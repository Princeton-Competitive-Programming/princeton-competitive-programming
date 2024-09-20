---
permalink: /fall24/week2_learn
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 2" %}

Welcome to the second week of competitive programming of the Fall of
2024! Today's problem solving session will be about sorting algorithms
and divide and conquer. As you'll see, the focus won't be exactly on
applying sorting algorithms to sort data, but rather to see how
sorting (and the concept of divide and conquer, central to algorithms
like merge sort or quick sort) can be used to solve all sorts of
problems.

Before reading a problem, read its accompanying description available
below. Work through the problems one by one, i.e. don't try working on
B before solving A, C before solving A, etc.

But first, if this is your first time ever in one of our
competitive programming sessions, please follow the instruction on our
new [introduction guide]({{ site.baseurl }}/intro_guide) to get
started. Once you're done, feel free to come back here.

## Problem A - Exam Room

In this problem you'll have to apply sorting plus a simple
calculation. Read the problem now if you haven't already.

The size of the input $n$ can go up to $10^5$, so recall that this
means your solution should work in $\Theta(n \log n)$ time or better.

In this first problem the only trick you need to know is how to
sort. You shouldn't implement a sorting algorithm from scratch, use
the deafult sorting algorithm from your favorite programming
language. Here is a [link](https://usaco.guide/bronze/intro-sorting)
where you can learn about this (select your language at the top).

## Problem B - Pizza Line

Read the problem now if you haven't already.

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
this, read the problem.

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

## Problem E - Permutation Graph

If you got here and solved all the previous problems, great job! If
you haven't solved one of the previous problems go back and solve it
first. The following problem is a challenge. It's much harder than the
previous problems and requires some more advanced knowledge (namely
the notion of graph and some basic graph algorithms). There are
different ways of solving it, but one of them uses divide and conquer
to simplify it. Read the problem and think about it.