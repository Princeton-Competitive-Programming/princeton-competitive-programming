---
permalink: /basic_ds_f23
layout: page
---

{% include main_title.html text="Fundamental Data Structures" %}

## Hints for problem A. New Netids

This problem is supposed to be an straightforward application of a set
data structure. Regardless of what language you are using there is
probably a data structure in its standard library (probably called
something close to *set*) that supports inserting and checking if an
element is in it. To solve this problem you should learn how to use it
and use it.

## Hints for problem B. Word Game

This is also supposed to be a straightforward application of a data
structure, but of a map/dictionary/symbol table. First insert the
input into the data structure using the words as keys and the values
as a count of their frequency, and then go through the input again to
tally up the points. To solve this problem you should learn how to use
the default map/dictionary/symbol table data structure from your
favorite programming language and then use it.

## Hints for problem C. Restoring the Duration of Tasks 

Another problem for you to learn how to use a data structure: a
queue. To solve it you have to simulate this process, by keeping track
of the current time:

* Take a task from the queue
* Take as time the maximum from the current time and from the arrival time of the task
* Subtract the current time from the time when the task was done
* Replace the current time with the time the task was done
* If there is a task in the queue, go to item 1

## Hints for problem D. Social Network

This problem is an implementation problem, you don't need to think too
much about it. You have to implement a data structure that looks like
a stack (so you can see the most recent conversation on the screen and
add new conversations if there are less than k), but where you have
arbitrary access to any element (so you can swap and shift).

## Hints for problem E. Greg and Array

This is the most challenging problem and uses a technique that is not
usually super well-known called *difference arrays*. Make sure you
know how it works first ([here is an article about
it](https://codeforces.com/blog/entry/78762)). Then to apply it to
this problem you have to do it twice, once to each of the m
operations, and then you have to use a "difference array of difference
arrays" approach to apply each one of the k queries. It's a bit
tricky, but it's very worth it once you solve it.