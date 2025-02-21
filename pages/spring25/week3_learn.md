---
permalink: /spring25/week3_learn
layout: page
---

{% include main_title.html text="Spring 25 - Learn Division Week 3" %}

Welcome to another week of competitive programming of Spring 2025!
Today's problem solving session will focus on **fundamental data
structures**. You will be using things like stacks, heaps, and binary
search trees.

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

This week, we focus on efficiently handling queries using built-in
data structures in Java, including `Stack`, `Queue`, `TreeSet`,
`TreeMap`, and `PriorityQueue` (i.e. a heap). These structures allow us to
efficiently manage and process data while solving competitive
programming problems. Understanding how to leverage these built-in
classes will help us implement efficient solutions.

Here is an overview of these with some Java code samples.

#### Stack (LIFO Order)
A `Stack` is a Last-In-First-Out (LIFO) data structure that allows push and pop operations.

```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(5);
        stack.push(10);
        System.out.println(stack.pop()); // 10
        System.out.println(stack.peek()); // 5
    }
}
```

#### Queue (FIFO Order)
A `Queue` follows a First-In-First-Out (FIFO) approach.

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();
        queue.offer(1);
        queue.offer(2);
        System.out.println(queue.poll()); // 1
        System.out.println(queue.peek()); // 2
    }
}
```

#### TreeSet (Sorted Set)
A `TreeSet` maintains elements in sorted order and provides logarithmic time complexity for operations.

```java
import java.util.TreeSet;

public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> treeSet = new TreeSet<>();
        treeSet.add(5);
        treeSet.add(1);
        treeSet.add(10);
        System.out.println(treeSet.first()); // 1
        System.out.println(treeSet.last()); // 10
    }
}
```

#### TreeMap (Sorted Key-Value Store)
A `TreeMap` is a sorted key-value store, useful for range queries.

```java
import java.util.TreeMap;

public class TreeMapExample {
    public static void main(String[] args) {
        TreeMap<Integer, String> treeMap = new TreeMap<>();
        treeMap.put(2, "B");
        treeMap.put(1, "A");
        treeMap.put(3, "C");
        System.out.println(treeMap.firstEntry()); // 1=A
        System.out.println(treeMap.lastEntry()); // 3=C
    }
}
```

#### PriorityQueue (Heap)
A `PriorityQueue` provides a min-heap or max-heap implementation.

```java
import java.util.PriorityQueue;

public class PriorityQueueExample {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(); // Min-heap
        pq.offer(10);
        pq.offer(5);
        pq.offer(20);
        System.out.println(pq.poll()); // 5 (smallest element)
    }
}
```

These data structures form the backbone of efficient algorithms in
competitive programming. Mastering their applications will help you
solve a variety of query-based problems effectively.

## Problem A: New Netids

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/590134/problem/A). Read
it and then come back here.

Given the constraints, you need to solve this in time $\Theta(q \log
q)$ or better. Think about how to do this using some of the data
structures mentioned above. If you are stuck, the next paragraph gives
a big hint.

To efficiently handle login credentials, we need a data structure that
supports fast insertions and lookups. A `TreeMap<String, String>` in
Java allows storing netids as keys and passwords as values with a time
complexity of \( O(\log n) \) for both operations.

--

## Problem B: Pizza Lines

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/590134/problem/B). Read
it and then come back here.

The problem requires us to efficiently find the first taller student
in front of a given student. A naive approach of checking every
student ahead would be too slow \( O(n^2) \). Instead, we want a
solution running in \( O(n) \) time. Think about how to do this using
some of the data structures mentioned above. If you are stuck, the
next paragraph gives a big hint.

To solve the problem efficiently, use a `Stack<Integer>` to keep track
of indices of students. Iterate through the array from left to right,
maintaining a decreasing stack so that when a taller student appears,
all shorter students behind them can be updated.

---

## Problem C: Word Game

Note that this problem has a multitest case structure, meaning that
your program has to process and solve multiple test cases.

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/590134/problem/C). Read
it and then come back here.

Given the constraints, you need to solve this in time $\Theta(n \log
n)$ or better. Think about how to do this using some of the data
structures mentioned above. If you are stuck, the next paragraph gives
a big hint.

This is also supposed to be a straightforward application of a data
structure, but of a map/dictionary/symbol table. First insert the
input into the data structure using the words as keys and the values
as a count of their frequency, and then go through the input again to
tally up the points. To solve this problem you should learn how to use
the default map/dictionary/symbol table data structure from your
favorite programming language and then use it.

--

## Problem D: T-shirt Buying

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/590134/problem/D). Read
it and then come back here.

Given the constraints, you need to solve this in time $\Theta(n \log
n)$ or better. Think about how to do this using some of the data
structures mentioned above. If you are stuck, the next paragraph gives
a big hint.

To solve the problem efficiently, use three `PriorityQueue<Integer>`
structures (one for each color). Insert t-shirt prices into the
respective `PriorityQueue` based on front and back colors. For each
buyer, retrieve and remove the lowest available price for their
preferred color using `poll()`.

---

## Problem E: Greg and Array

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/590134/problem/E). Read
it and then come back here.

This is the most challenging problem and uses a technique that is not
usually very well-known called *difference arrays*. Make sure you
know how it works first ([here is an article about
it](https://codeforces.com/blog/entry/78762)). Then to apply it to
this problem you have to do it twice, once to each of the m
operations, and then you have to use a "difference array of difference
arrays" approach to apply each one of the $k$ queries. It's a bit
tricky, but it's very worth it once you solve it.