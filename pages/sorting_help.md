---
permalink: /sorting_f23
layout: page
---

{% include main_title.html text="Sorting Problems" %}

## Hints for problem A. Gravity Flip

It's not hard to see that this will end up sorting all the amounts in
increasing order. So you only have to sort the input. Make sure you
know how to use the default sorting methods from your favorite
language: [here is a helpful
link](https://usaco.guide/bronze/intro-sorting).

## Hints for problem B. Princeton Parking Problem

There is a dent if the position of two consecutive cars is
overlapping. So to solve this it might help to put cars in order and
then check if any pair of consecutive cars overlaps.

## Hints for problem C. Remove Smallest

We can only remove elements that are consecutive. So it might help to
put all elements in order and then check if we can remove them from
smallest to largest.

## Hints for problem D. Parity Sort

Note that after doing any number of operations, all the indices
containing odd numbers still contain odd numbers and all indices
containing even numbers also contain even numbers. This observation
should tell you something about whether you can do it or not (look at
the sorted array and see if it satisfies it).

## Hints for problem E. Thematic Contests

This is more challenging than the previous ones, so we won't give any
major hints. The one observation that might help is that because you
have to double the number of problems in each contest, you can only
have at most log(10^9) contests, which is a small number.
