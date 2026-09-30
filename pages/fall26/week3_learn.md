---
permalink: /fall26/week3_learn
layout: page
---

{% include main_title.html text="Fall 26 - Learn Division Week 3" %}

Welcome to another week of competitive programming of Fall 2026!
Today's problem-solving session will focus on binary search. You
probably know about binary search as a way to find elements in an
array, but we will use this concept in a more general way today.

But first, if this is your first time ever in one of our competitive
programming sessions, please see our [introduction guide]({{
site.baseurl }}/intro_guide) to get started. Once you're done, feel
free to come back here.

Feel free to work together with a friend or two, this is supposed to
be a collaborative environment. Also, if you are stuck or have
questions, don't keep them to yourself!  Talk to other people! If you
are not sure who to talk to, ask on discord.

## Problem A - Course Selection

Start by reading the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/720697/problem/A).

This is a typical application of binary search. Binary search is
useful when dealing with sorted data, where elements are arranged in a
known order. It allows us to efficiently search for an element or
determine if it exists in a dataset by repeatedly dividing the search
space in half.

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

Since the algorithm reduces the search space by half each time, the
worst-case running time is \( \Theta(\log N) \).

Here is a quick implementation of the algorithm, along with some code
that reads a target and a sorted array from the standard input. Feel
free to use this code and modify it in the following problems.

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

Now implement a solution to problem A using the above. Given the
constraints, you need to solve it in time $\Theta(N \log Q)$ or
$\Theta(Q \log N)$ or better.

## Problem B - Paw Points

The next problem you will work on is another typical application of
binary search, but it will be less obvious than the previous one. You
can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/720697/problem/B). Read
it and then come back here.

As you can see, the problem is pretty similar in structure to the
previous one (and it's recommended that you reuse the code from
problem A). Indeed, given the constraints, you need to solve this in
time $\Theta(N \log Q)$ or $\Theta(Q \log N)$ or better.

There are a few key differences though. First, notice that the array
isn't necessarily sorted this time. This isn't a big deal, you can
easily sort the array using your favorite language's sorting
primitive. For example, in Java this would be `Arrays.sort(arr)`. If
you want to use binary search on a problem always make sure that the
array is sorted!

Now the other key difference is that it is not as obvious how to use
binary search since we are not looking for a specific element. We are
looking for the largest element smaller than or equal to a given
target (and note that you can have repeated elements, which makes it
even trickier!), since that's the most expensive item one can buy and
thus we can buy any item cheaper than that too.

We'll leave the remaining details for you to figure out.

## Problem C - Dining Halls

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/720697/problem/C). Read
it and then come back here.

This problem is the first one where you won't use binary search on an
array directly. Instead, it requires a technique known as "binary
search the answer", which is a very powerful and useful technique you
will need for this problem.

The idea is that instead of binary searching over an array, we binary
search over the space of *possible answers* to the problem. This works
whenever two things hold:

* We can turn the problem into a decision problem, i.e. write a
  `check(k)` method that tells us whether some candidate answer $k$ is
  feasible.
* That decision is monotone (i.e. once `check(k)` becomes true it
  stays true for all larger, or all smaller, values of $k$).

If both hold, we can binary search over $k$ using `check` at each step
instead of comparing array elements, the same way we compared
`arr[mid]` to the target before.

Given the constraint on $n$ and $t$, you need a solution that runs in
$\Theta(n \log t)$ or better. To apply the technique here we need:

* Turn the problem into a decision problem. In this case it should be
  something like: given a possible answer $k$, can we determine
  whether the $n$ cooks can make $t$ meals in $k$ time?
* Check that the answer is monotone. In this case, if the $n$ cooks
  can make $t$ meals in $k$ time, then they can definitely make $t$
  meals in $k'$ time if $k' \geq k$. Conversely, if the $n$ cooks can't
  make $t$ meals in $k$ time, then they can't make $t$ meals in $k'$
  time if $k' \leq k$.

So now all you need to solve this problem is implement the `check`
method and determine appropriate upper and lower bounds for any
possible answer. With the latter, be careful with overflows (the
answer might not fit in an integer, in Java you can use `long`)!

## Problem D - Predator or Prey

One last problem for you to work on. You can find the [problem
description
here](https://codeforces.com/group/hNnRWqFua0/contest/720697/problem/D).
Read it and then come back here.

Given the constraint on $n$, you need a solution that runs in
$\Theta(n \log n)$ or better. We won't give a full hint this time, but
here are a couple of small nudges if you're stuck. Both of them go
back to the ideas from problems A and B:

* For a given animal, the animals it preys on are those whose predator
  factor falls in a certain range of values. Can you write down that
  range? Then the answer is the number of animals with a factor in
  that range.
* Counting the elements of a sorted array that fall inside a range is
  just two binary searches.