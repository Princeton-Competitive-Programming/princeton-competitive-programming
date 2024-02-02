---
permalink: /ps_s24
layout: page
---

{% include main_title.html text="Prefix Sums" %}

Prefix sums are a powerful technique for efficiently solving problems
related to array manipulation and queries about sums of elements. The
core idea behind prefix sums is to preprocess an array in such a way
that queries asking for the sum of elements in a subrange (i.e., the
sum of elements from index i to j in the array) can be answered
quickly, in constant time after the preprocessing step. This
preprocessing involves constructing a new array where each element at
index i represents the sum of all elements in the original array from
the start up to index i. This means that the i-th element of the
prefix sum array stores the sum of elements from the beginning of the
array up to and including the i-th element of the original array.

Once the prefix sum array is computed, the sum of elements in any
subrange can be found by a simple subtraction: the prefix sum at the
end of the range minus the prefix sum just before the start of the
range (with special handling when the start of the range is at the
beginning of the array). This technique reduces the time complexity of
answering sum queries from O(s) per query (where s is the number of
elements in the subrange) to O(1) after an O(n) preprocessing time
(where n is the size of the original array). Prefix sums are not only
limited to sum queries but also extend to various applications, such
as calculating moving averages, handling range update queries in
mutable arrays, and solving problems in other domains like
computational geometry and dynamic programming.

For a more detailed description of this technique, here is a [good
article](https://usaco.guide/silver/prefix-sums?lang=java).

## Hints for problem A. Nassau Street

This problem asks you to implement the core idea of prefix sums. After
reading the description above you should have all the theoretical
tools needed to do so. Note that you need to build the array of prefix
sums in linear time in order for this to be efficient.

The implementation is mostly straightforward once you understand the
idea, the only thing to keep in mind is that it is easy to make
off-by-one errors. For example, one common mistake is to not include
the first element of the range when computing a sum.

## Hints for problem B. Hoof, Paper, Scissors

This problem is still an application of the prefix sums technique, but
it is slightly disguised. What you really want to do is count how many
Hoofs, Papers, Scissors are in each prefix or suffix. Can you use the
idea of prefix sums to do so?

## Hints for problem C. The Treasure Map Queries

Now that you mastered using this technique in 1D arrays, you will try
to upgrade it to support 2D arrays. The idea is exactly the same: you
want to compute a prefix array with two coordinates i, j, that
computes the sum of all the elements in the subrectangle with corners
(0, 0) and (i, j). Now given any subrectangle, you want to compute its
sum by combining the prefix sums of certain coordinates. It's a little
trickier than the 1D case, but it is a good exercise to think about.

If you want to see the answer, this [link](https://usaco.guide/silver/more-prefix-sums?lang=java) has a great write-up.

## Hints for problem D. Good Subarrays

This is a trickier problem that isn't a direct application of prefix
sums. You will still need to use the concept of prefix sums to solve
it, but it's not as easy as the previous problem.

The first tip is to try to understand the definition "good subarray" a
bit better. The main difficulty is that the definition seems "2d",
meaning it depends on the two endpoints of the array. See if you can
"decouple" it, meaning combining two independent statements about each
endpoint. Then, note that a prefix sum array doesn't have to be exactly
sums of prefixes of the array, it could have more information in it.

The hints are a bit "cryptic" by design, there is no easy way to hint
something without giving away the answer. It's the kind of problem you
should think about for a bit and if you are stuck for a while ask for
help.