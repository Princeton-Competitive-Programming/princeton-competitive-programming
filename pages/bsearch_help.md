---
permalink: /binary_search_f23
layout: page
---

{% include main_title.html text="Binary Search Techniques" %}

## Hints for problem A. Course Selection

The problem requires efficiently determining the existence of courses with specific course numbers within a sorted list of course numbers. To solve this, a binary search approach is employed. After reading the input data, use binary search to check if a query course number exists in the list. Here is some pseudocode to help you implement binary search

<pre><code class="bg-light p-3">function binary_search(array, target):
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
    
    return -1  # Your target isn't in the array.</code></pre>

Don't just implement this in your favorite language! Make sure you understand what is going on before implementing it.
