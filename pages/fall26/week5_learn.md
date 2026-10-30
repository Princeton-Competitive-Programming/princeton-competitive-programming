---
permalink: /fall26/week5_learn
layout: page
---

{% include main_title.html text="Fall 26 - Learn Division Week 5" %}

Welcome to another week of competitive programming of Fall 2026! Today's
problem-solving session will focus on **dynamic programming**.

But first, if this is your first time ever in one of our competitive
programming sessions, please see our [introduction guide]({{
site.baseurl }}/intro_guide) to get started. Once you're done, feel
free to come back here.

To make the most out of your experience in these sessions you should
attempt to solve the problems one by one, i.e. don't try working on B
before solving A, C before solving A, etc. You don't have to solve all
the problems, you will be learning something even if you only try to
solve a single problem.

Feel free to work together with a friend or two, this is supposed to
be a collaborative environment. Also, if you are stuck or have
questions, don't keep them to yourself!  Talk to other people! If you
are not sure who to talk to, ask on discord.

## Problem A. Fibonacci

This is the simplest, most common example of dynamic programming out
there. Dynamic programming is a very popular problem-solving technique
that decomposes a problem into subproblems and then tries to avoid
recomputing the solution to the same subproblem twice. It's very hard
to learn dynamic programming generically, it's a concept you learn by
looking at many problems, and then you eventually start noticing
similar patterns in new problems. So let's start with the simplest
example.

The Fibonacci numbers are defined by $F(0) = 0$, $F(1) = 1$ and
$F(n) = F(n-1) + F(n-2)$ (in this problem, we compute everything
modulo 1009, but let's ignore that for a moment). The recurrence
immediately gives us a recursive solution, but it is terribly slow,
because it recomputes the same values over and over again (for
example, $F(n-2)$ is computed once by $F(n)$ and once more by
$F(n-1)$, and this blows up exponentially). The fix is to remember the
answer to each subproblem the first time we compute it. There are two
standard ways to do so.

The first one is **memoization**: we keep the recursive solution, but
we store the result of each call in a table. Before computing the
answer to a subproblem we check the table, and if it is already there
we return it immediately instead of recursing again.

The second one is **bottom-up**: we get rid of the recursion and
instead fill the table directly, in an order such that everything an
entry needs was already computed. Here we would fill the entries for
$0, 1, 2, \dots$ in increasing order, since $F(i)$ only needs the two
entries right before it.

Both are perfectly fine and run in $\Theta(n)$ (and the statement
asks for exactly that). With $n$ up to $10^5$, be careful with the
recursive version, since a very deep recursion can overflow the stack
in Java, so we recommend the bottom-up one here. Most dynamic
programming problems follow the same recipe:

1. Define what each table entry means (here, the $i$-th entry is the
   $i$-th mod-Fibonacci number).
2. Write a recurrence that computes an entry from smaller ones, plus
   the base cases that don't need a recurrence.
3. Fill in the table in an order that respects the recurrence.

Now read the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/728817/problem/A)
and implement it. If you have never used the modulo operator, the
statement gives you a useful property: you can take the remainder
after every addition, so the numbers never get large. If you are
having trouble with it, ask for help (during the event or on discord).

## Problem B. Cheesiest Slice

The hard part of most dynamic programming problems is deciding what a
table entry should *mean*. A very common trick, when you are building a
sequence out of a list, is to define the entry by fixing the *last*
element you chose: the entry for position $i$ is the best answer among
all the sequences that end exactly at position $i$. Then, to compute
it, you ask "what could have come right before the last element?", and
the answer to that question is a smaller subproblem that is already in
the table. Finally, remember that since you don't know in advance which
element will be the last one, the final answer is usually found by
looking at *all* the entries, not only the last one.

Now read the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/728817/problem/B).
Given that $n \leq 10^3$, you need a solution that runs in
$\Theta(n^2)$ or better (this is a classic problem, known as the
*longest increasing subsequence*).

Here are some hints, in case you need them:

* Trying all subsets of slices is far too slow. Instead, let the table
  entry for slice $i$ be the largest number of slices Susan can eat if
  slice $i$ is the last one she eats.
* Which slices could Susan have eaten right before slice $i$? What
  does that tell you about the best answer ending at slice $i$?
* Don't forget that slice $i$ by itself is always a valid option.

## Problem C. Cheesiest Slice II

Your table usually tells you the *value* of the best answer, but
sometimes you also need the answer itself. The standard way to get it
is to store, along with each entry, which choice produced it. At the
end, you can walk backwards through those choices to rebuild the
answer.

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/728817/problem/C).
This is the same setup as the previous problem, so the same running
time of $\Theta(n^2)$ is expected. Solve the previous problem first,
then here are some hints:

* What extra piece of information would you need to remember for each
  slice to be able to tell which slice came right before it?
* Where do you start the walk backwards, and how do you know when to
  stop?
* The walk visits the slices in the opposite order to how Susan eats
  them.

## Problem D. Basketball Exercise

Two more ideas will be useful for this problem. First, sometimes the
table entry needs one extra piece of information in addition to the
position, like which of a few categories the last chosen element
belongs to. In that case you simply keep one entry per category. Second,
if the recurrence needs the maximum over *all* earlier entries, and
that set of entries only grows as you go from left to right, you don't
need to recompute the maximum from scratch each time: you can keep a
running maximum and update it as you go.

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/728817/problem/D).
Given that $n \leq 10^5$, you need a solution that runs in
$\Theta(n)$. Some hints:

* Think about the previous problems and fix the *last* student that
  gets chosen. What do you need to know about them to extend the team?
* Which students are allowed to come right before a given student?
  Write the recurrence that comes out of this, and note that it is
  correct but has a running time of $\Theta(n^2)$.
* Use the running maximum idea above to speed it up. Be careful about
  *when* you update it, since a team cannot use two students from the
  same position.
* A team doesn't have to use the last position. Also, the answer can
  be larger than an `int` can hold, so use `long`.

## Problem E. Boredom

Many dynamic programming problems boil down to walking through an
ordered list of items and making a *take-or-skip* decision for each
one, where taking an item restricts which other items you can take. If
the restriction only involves the item right next to it, the table
entry for item $i$ only needs to look at the entries for $i - 1$ and
$i - 2$.

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/728817/problem/E).
Both $n$ and the values are at most $10^5$, so the goal is to run in
$\Theta(n + \max a_i)$. Some hints:

* It doesn't matter which element is which, we only need to know how
  many 1s, 2s, ... are there. Start by collecting these counts in a
  new array.
* If you decide to take a value $v$, how many points do you get in
  total from it? What happens to the values next to it?
* Now you have an ordered list of items (the values $1, 2, 3, \dots$)
  where taking an item prevents taking its neighbors. Can you set up
  the take-or-skip recurrence?
* The answer can be larger than an `int` can hold, so use `long`.
