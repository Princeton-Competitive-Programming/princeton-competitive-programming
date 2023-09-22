---
permalink: /binary_search_f23
layout: page
---

{% include main_title.html text="Binary Search Techniques" %}

## Hints for problem A. Course Selection

The problem requires efficiently determining the existence of courses with specific course numbers within a sorted list of course numbers. To solve this, a binary search approach is employed. After reading the input data, use binary search to check if a query course number exists in the list. Here is some pseudocode to help you implement binary search

<pre class="bg-light p-3">function binary_search(array, target):
    left = 0
    right = array.length - 1
    
    while left <= right:
        mid = left + (right - left) // 2
        
        if array[mid] == target:
            return mid  # You found your target!
        elif array[mid] < target:
            left = mid + 1  # Discard the left half
        else:
            right = mid - 1  # Discard the right half
    
    return -1  # Your target isn't in the array.</pre>

Don't just implement this in your favorite language! Make sure you understand what is going on before implementing it.

## Hints for problem B. Interesting drink

The problem involves Vasiliy's plan to buy his favorite drink,
"Beecola," for q consecutive days from n different shops with varying
prices. To efficiently determine the number of shops where he can buy
a bottle of the drink within his daily spending limit, we sort the
prices of the bottles in non-decreasing order. Then, for each day, we
use binary search to find the maximum affordable price, identifying
the last shop where he can make the purchase. The number of such shops
is index + 1, where index is the result of the binary search. This
approach, with a preprocessing step of sorting prices, ensures quick
answers for each day's shopping plan and has a time complexity of O(n
log n) for preprocessing and O(q log n) for the binary search portion,
making it efficient for large datasets.

Note that the binary search method you have to implement to solve this
problem is a bit different from the previous one. In this problem you
are not looking for an element in an array, but rather what is the
largest index whose value is less than or equal to the target value.

## Hints for problem C. The Meeting Place Cannot Be Changed

In this problem, friends are located at different positions along a
straight road, each with a specific maximum speed they can move. The
task is to calculate the minimum time required for all friends to
gather at a single point on the road. This means determining the
optimal meeting point and the time it takes for each friend to reach
that point while respecting their maximum speed.

To tackle this efficiently, employ a binary search approach on the
answer. Let's try to check if it is possible to meet within t
seconds. In this time, i-th friend can get anywhere within the segment
[x_i - t*v_i, x_i + t * v_i]. For the meeting to be possible, there
must be a point common to all these segments, that is, their
intersection must be non-empty. We can do this in linear time (try to
think how!) If we verify that the friends can me within t seconds,
then they definitely can meet within >t seconds, if they can't meet
within t seconds then they can't meet within <t seconds. We can use
this intuition to implement our binary search.

## Hints for problem D. Kayaking Trip

Again the trick here is to binary search over the answer (i.e. the
maximum speed of the slowest kayak). To check if we can assign
participants to kayaks such that the slowest kayak has speed at least
v, greedily assigning people to kayaks. Think about what is a good
greedy strategy to do this. For example, if two weak participants can
be a assigned to some kayak and we have at least two weak participants
left to assign, then we should do so. It's a little tricky, so think
well how to do this optimally!