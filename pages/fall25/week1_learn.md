---
permalink: /fall25/week1_learn
layout: page
---

{% include main_title.html text="Fall 25 - Learn Division Week 1" %}

Welcome to the first week of competitive programming of the Fall of
2025! Today's problem-solving session will be a sort of warm up
session, with problems designed to help you get used to the format of
the event.

If this is your first time ever in one of our competitive programming sessions,
make sure you have completed our [introduction guide]({{ site.baseurl
}}/intro_guide) before getting started.

Here is the [link](https://codeforces.com/group/hNnRWqFua0/contest/636300) to this week's problem set.

## Problem 1 - Target Practice

This is an implementation problem, you don't have to do anything too
clever. Just follow the instructions on the problem statement.

## Problem 2 - Shortest Substring

Scan the string from left to right and think about what you should do every time
you see two consecutive different characters.

## Problem 3 - Biggest Island

In this problem you might need to use a data structure to help
you. You need something that lets you assign elements to groups, and
then count the number of groups.
([hint](https://algs4.cs.princeton.edu/15uf/)).

## Problem 4 - Strictly Increasing 

Spoiler hint: Treat the feasibility as two independent checks you can maintain under point updates — (1) the array must remain strictly increasing, which you can track by keeping a small set/counter of "broken" adjacent positions $i$ where $a_i \ge a_{i+1}$ (only neighbors of the updated index can change), and (2) the total number of integers you can squeeze in between existing values equals the sum of gap capacities $\sum_{i=1}^{n-1}\max(0,\;a_{i+1}-a_i-1)$, which you can keep as a single running total by subtracting the old contributions of gaps $(i-1,i)$ and $(i,i+1)$ and adding their new ones after each update. Answer "YES" if and only if there are no broken positions and the running total $\ge k$.