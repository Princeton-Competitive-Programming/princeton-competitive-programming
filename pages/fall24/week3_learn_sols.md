---
permalink: /fall24/week3_learn/solutions
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 3 - Solutions	" %}

Problem set [link](https://codeforces.com/group/hNnRWqFua0/contest/553384).

## Problem A - [Parity Sort](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/A)

Note that after doing any number of operations, all the indices
containing odd numbers still contain odd numbers and all indices
containing even numbers also contain even numbers. So sort the whole
array and then check if the indices of odd elements in the original
array are still contain odd elements, and same for evens.

## Problem B - [Course Selection](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/B)

For each of the $Q$ operations, perform one binary search on the list
of courses.

## Problem C - [Dining Halls](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/C)

The solution was basically described in the original notes. Here is a
reproduction of the notes with some extra details.

To apply the binary search the answer technique here we need
two things:

* Turn the problem into a decision problem (i.e. `check` method like
in the first pseudocode example from the reading). In this case it
should be something like: given a possible answer $x$, can we
determine whether the $n$ cooks can make $t$ meals in $x$ time?
* We need the answer to be monotone (i.e. either increasing or
decreasing). In this case, if the $n$ cooks can make $t$ meals in $x$
time, then can definitely make $t$ meals in $x'$ time if $x' \geq
x$. Conversely, if the $n$ cooks can't make $t$ meals in $x$ time,
then can't make $t$ meals in $x'$ time if $x' \leq x$.

To check whether we can make $t$ meals in $x$ time, note that the
$i$th cook can make $\lfloor x / k_i \rfloor$ meals, so if you sum
this quantity for all cooks and get a value greater than $t$, then the
answer is yes.

Here is the solution in Java:

```java
public static void main(String[] args) {
    // Assume input was read and stored in n, t and array k
    // Binary search over time
    long lo = 1;
    long hi = 1000000000 * t; // Maximum possible value is 10^9 * t
    long result = hi;
 
    while (lo <= hi) {
        long mid = lo + (hi - lo) / 2;
        if (checl(mid, t, k)) {
            result = mid;  // Try for a smaller time
            hi = mid - 1;
        } else {
            lo = mid + 1;
        }
    }
        
    System.out.println(result);
}
 
public static boolean check(long x, long t, long[] k) {
    long meals = 0;
    for (long cookTime : k) {
        meals += x / cookTime;
        if (meals >= t) return true;  // Early exit if enough meals are made
    }
    return meals >= t;
}
```

(for those that are taking/took COS226, notice the similarity of the
binary search with `firstIndexOf`/`lastIndexOf` of the autocomplete
assignment)

## Problem D - [Kayaking Trip](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/D)

Most of the solution was in the original notes, so here is a
reproduction of the notes with some extra details.

The trick here is to binary search over the answer (i.e. the maximum
speed of the slowest kayak): define a `check` function and make sure
it is monotone. The natural `check` function is: given a speed $v$,
can we distribute the participants such that the slowest kayak has
speed at least $v$? It's clear that this is monotone.

Now, the problem we are trying to solve is the following: given a
speed of $v$, can we assign people to kayaks such that each has speed
at least $v$? Take the kayak with lowest $c$. It will have to be
assigned two people, so give it the two people with lowest strengths
such that the resulting velocity is at least $v$. Repeat this for each
kayak until we get stuck, i.e. no matter what people we pick, the
kayak speed is less than $v$.

## Problem E - [The Meeting Place Cannot Be Changed](https://codeforces.com/group/hNnRWqFua0/contest/553384/problem/E)

Let's try to check if it is possible to meet within $t$ seconds. In
this time, the $i$th friend can get anywhere within the segment
$[x_i - t\cdot v_i, x_i + t \cdot v_i]$. For the meeting to be
possible, there must be a point common to all these segments, that is,
their intersection must be non-empty. We can do this in linear time
(it's very similar to the Class Schedule problem from last week!). If
we verify that the friends can me within $t$ seconds, then they
definitely can meet within $> t$ seconds, if they can’t meet within
$t$ seconds then they can’t meet within $< t$ seconds.
