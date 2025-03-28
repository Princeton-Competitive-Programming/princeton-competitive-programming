---
permalink: /spring25/week6_compete
layout: page
---

{% include main_title.html text="Spring 25 - Compete Division Week 6" %}

Welcome to another week of competitive programming in Spring 2025! In
this session, we'll focus on **range data structures**, in particular
on segment trees (but you can solve these problems using other data
structures). These techniques allow you to answer range queries and
perform range modifications efficiently.

## Introduction

### Segment Trees

(note, we recommend reading this
[link](https://usaco.guide/CPH.pdf#page=99) for a more detailed
description of this concept).

Consider the following problem:

You are given a sequence $s$ of $ N $ integers. Your task is to support two types of operations:
- **Sum Query:** Compute the sum of the elements on a segment $[a, b]$ of the sequence, so $s_a+s_{a+1} + \ldots + s_{b}$
- **Point Update:** Change the value at a specific position in the sequence, so for example given $i$ and $v$, set $s_i$ to $v$.

Segment trees allow you to efficiently solve the above problem (and
variations with different query operations) by breaking the array into
segments and storing aggregate values for each segment. Instead of
processing the whole array for every query, the tree structure lets
you quickly combine results from relevant segments.

Initially, the entire array is considered as one segment - the root of
the tree. This segment is then split into two halves, which form the
left and right children of the root. Each of these halves is further
divided into two segments, and this process continues until the base
case is reached—segments of length one (individual elements).

The segment tree is typically stored in an array, where:
- The **root** of the tree is at index 1.
- For any node at index `i`, its **left child** is at `2*i` and its **right child** is at `2*i + 1`.
- Conversely, the **parent** of a node at index `i` is at `i/2` (using integer division).

This array-based representation simplifies navigation between nodes
and keeps the memory overhead low. The leaves of the tree represent
individual elements of the original array, while each internal node
stores the aggregate value (e.g., the sum) of its child segments. When
you build the tree, you recursively divide the array into two halves
until you reach single elements, then combine these values as you move
up the tree. Queries then work by checking if a segment is fully
inside or outside the query range, combining values from only the
segments that matter.

For example, here’s a simplified Java snippet for building and
querying a segment tree that computes sums:

```java
int[] segTree;
int n;

// Builds the segment tree for sum queries.
// 'idx' is the current tree index, [l, r] is the current range in the array.
void build(int[] arr, int idx, int l, int r) {
    if (l == r) { // Leaf node: store element value.
        segTree[idx] = arr[l];
        return;
    }
    int mid = (l + r) / 2;
    build(arr, 2 * idx, l, mid);        // Build left child.
    build(arr, 2 * idx + 1, mid + 1, r);  // Build right child.
    segTree[idx] = segTree[2 * idx] + segTree[2 * idx + 1]; // Merge results.
}

// Queries the segment tree to sum values in the range [ql, qr].
// 'idx' is the current tree index, [l, r] is the segment range.
int query(int idx, int l, int r, int ql, int qr) {
    if (ql > r || qr < l) return 0;         // No overlap.
    if (ql <= l && r <= qr) return segTree[idx]; // Total overlap.
    int mid = (l + r) / 2;
    // Partial overlap: query both children.
    return query(2 * idx, l, mid, ql, qr) + query(2 * idx + 1, mid + 1, r, ql, qr);
}
```

In this code:
- **Building the tree:**  
  The `build` function recursively divides the array into halves until reaching a single element (leaf node), then backtracks and combines these segments by summing them.
  
- **Querying the tree:**  
  The `query` function checks if the current segment is completely outside, completely inside, or partially overlapping the query range, and then combines results accordingly.

This array-based segment tree representation leverages the simple
arithmetic of indices to navigate the tree efficiently, making both
construction and queries fast (typically $O(n)$ for building and
$O(\log n)$ for each query).

### Lazy Propagation

(note, we recommend reading this
[link](https://usaco.guide/CPH.pdf#page=268) for a more detailed
description of this concept).

Lazy propagation is an optimization technique (often used with segment
trees) to handle range updates efficiently. Instead of updating every
single element in a range immediately lazy propagation defers the
update until it's absolutely necessary, typically during a query. Here
is a more detailed description of how this works in segment trees.

When a range update is applied, you traverse the down the tree until
you find segments completely contained in the range to be
updated. Then, mark the current segment with a "lazy" value instead of
updating all elements immediately. This lazy value indicates that the
segment still needs to be updated.

When you later query a segment or need to update a part of it, you
first check for any pending lazy updates. If they exist, you "push"
these updates to the node's children and update the current node
appropriately. This ensures that the query reflects the correct value.

### Extra Resources

For a lot more detail and a lot of extra information on application
and more advanced variants see this
[link](https://cp-algorithms.com/data_structures/segment_tree.html).

---

## Problem A. Horace the Competitive Programming Tiger

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/599531/problem/A). Read
it and then come back here.

A segment tree that stores the XOR for each segment is ideal. Each
leaf corresponds to an element, and each internal node aggregates the
XOR of its children. When a point is updated, you simply update the
corresponding leaf and propagate the change up the tree. This setup
lets you answer XOR queries in logarithmic time.

---

## Problem B. Copying Data

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/599531/problem/B). Read
it and then come back here.

This problem is about range updates, so the key idea is to apply lazy
propagation. Instead of copying elements one by one, mark entire
segments with a lazy tag that represents a pending copy from $ a $
to $ b $ (you might have to carefully change the indices as you move
through the tree). Only when a query accesses a segment will the
pending copy be applied, ensuring that range copying is handled
swiftly.

Note that you don't need to implement the full range query method in
this problem, since only index queries can be performed.

---

## Problem C. Pillars

You can find the [problem description
here](https://codeforces.com/group/hNnRWqFua0/contest/599531/problem/C). Read
it and then come back here.

This problem doesn't seem to be about range queries at all! And in
fact it isn't! It's a dynamic programming problem: for each pillar,
compute the maximum jump sequence ending at that pillar. If you write
this DP update down and try to compute it directly, you will notice
that it takes quadratic time, which is too slow. You want to use a
segment tree to quickly query the best sequence length for all valid
previous pillars.

There is one other trick you need. Since the heights may be very
large, compress these values to use them effectively as indices in the
segment tree. Compressing just means storing a list of all $h$ values
so you can map a certain $h$ value to an integer $i$ between $1$
and $n$ that means that $h$ is the $i$ highest height.

---

Good luck with these challenges! Focus on understanding the core concepts behind segment trees and lazy propagation, and use these insights to guide your approach without relying on a full step-by-step solution.
```