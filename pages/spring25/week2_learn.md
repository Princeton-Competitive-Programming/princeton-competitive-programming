---
permalink: /spring25/week2_learn
layout: page
---

{% include main_title.html text="Spring 25 - Learn Division Week 2" %}

Welcome to another week of competitive programming of Spring 2025!
Today's problem solving session will focus on binary search. You
probably know about binary search as a way to find elements in an
array, but we will use this concept in a more general way today.

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

Today's session will be on binary search and some applications of this
concept. So let's start by reviewing it.

Binary search is useful when dealing with sorted data, where elements
are arranged in a known order. It allows us to efficiently search for
an element or determine if it exists in a dataset by repeatedly
dividing the search space in half.

Assume we are given as input a sorted array `arr` of size `N` and a
target value `x`. Our goal is to determine whether `x` exists in `arr`
and, if so, at what index. Binary search does this by iteratively
narrowing the search space by comparing the middle element with `x`
and adjusting the boundaries accordingly.

1. Sets two pointers: `low` at the beginning and `high` at the end of the array.
2. Finds the middle index `mid = (low + high) / 2`.
3. Compares `arr[mid]` with the target:
   - If `arr[mid]` is the target, return `mid`.
   - If `arr[mid]` is greater, search the left half (`high = mid - 1`).
   - If `arr[mid]` is smaller, search the right half (`low = mid + 1`).
4. Repeat until `low` exceeds `high`, i.e. there are no more valid elements left.

Since the algorithm reduces the search space by half each
the worst-case running time is \( \Theta(\log N) \).

### Implementation

Here is a quick implementation of the algorithm, along with some code
that reads a target and a sorted array from the standard input.

```java
import java.util.*;

public class Main {
    public static int binarySearch(int[] arr, int target) {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if      (arr[mid] < target) low = mid + 1;
            else if (arr[mid] > target) high = mid - 1;
            else return mid;
        }
        return -1;
    }
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int target = scanner.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        
        System.out.println(binarySearch(arr, target));
    }
}
```

Feel free to use this code and modify it in the following problems.

## Problem A - Course Selection

The first problem you will solve is a typical application of binary
search. You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/588421/problem/A). Read
it and then come back here.

Given the constraints, you need to solve this in time $\Theta(N \log
Q)$ or $\Theta(Q \log N)$ or better. Try to think how you could solve
it and then implement a solution, submit it and make sure it gets an
Accepted verdict (see our [introduction guide]({{ site.baseurl
}}/intro_guide) if you don't know what this means).

If you still need some extra help, here is a hint. The problem
requires efficiently determining the existence of courses with
specific course numbers within a sorted list of course numbers. After
reading the input data, use binary search to check if a query course
number exists in the list.

## Problem B - Paw Points

The next problem you will work one is another typical application of
binary search, but it will be less obvious than the previous one. You
can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/588421/problem/B). Read
it and then come back here.

As you can see, the problem is pretty similar in structure to the
previous one (and it's recommended that you reuse the code from the
previous problem). Indeed, given the constraints, you need to solve
this in time $\Theta(N \log Q)$ or $\Theta(Q \log N)$ or better.

There are a few key differences though. First, notice that the array
isn't necessarily sorted this time. This isn't a big deal, you can
easily sort the array using your favorite language's sorting
primitive. For example, in Java this would be `Arrays.sort(arr)`. If
you want to use binary search on a problem always make sure that the
array is sorted!

Now The other key difference is that it is not as obvious how to use
binary search since we are not looking for a specific element. We are
looking for the largest element smaller than or equal to a given
target (and note that you can have repeated elements, which makes it
even trickier!), since that's the most expensive item one can buy and
thus we can buy any item cheaper than that too.

We'll leave the remaining details for you to figure out.

## Problem C - Dining Halls

This problem is the first one where you won't use binary search on an
array. This problem requires a technique known as "binary search the
answer", which is a very powerful and useful technique you will need
for this and the remaining problems. First, read chapter 12 of these
[notes](https://darrenyao.com/usacobook/java.pdf#page=68).

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/588421/problem/C). Read
it and then come back here. Given the constraint on $n$ and $t$, you
need a solution that runs in $\Theta(n \log t)$ or better. The idea
you need here is similar to the example from the reading. To apply the
binary search the answer technique here we need two things:

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

## Problem D - Predator or Prey

One last problem for you to work on. This time we won't give any
hints, but you should be able to solve it with the ideas you developed
in the other 3. You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/588421/problem/D).
