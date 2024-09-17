---
permalink: /fall24/week1_learn/solutions
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 1 - Solutions" %}

Here is the
[link](https://codeforces.com/group/hNnRWqFua0/contest/549922) to all
the problems.

## Problem 1 - [Target Practice](https://codeforces.com/group/hNnRWqFua0/contest/549922/problem/A)

This was an implementation problem where you didn't really have to
worry about runtime of the solution.

The implementation should first read the number of test cases, and
then for each test case read 10 lines. To compute the answer to a test
case, one needs to iterate through all the elements, and for all the
`X` add the points corresponding to that location. There are many ways
of computing points, but here is a short one. If `X` is in row `i` and
column `j` (0-based) then there is a simple formula to compute the
score which is: $\min\{i, 9 - i, j, 9 - j\}$, which corresponds to
computing how far away from the center the point is.

Here is a possible solution in Java (notice that we need to do a
`nextLine` after reading the number of test cases).

```java
import java.util.Scanner;

public class TargetPractice {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        sc.nextLine(); // Consume the newline

        while (t-- > 0) {
            int totalPoints = 0;
            for (int i = 0; i < 10; i++) {
                String line = sc.nextLine();
                for (int j = 0; j < 10; j++) {
                    if (line.charAt(j) == 'X') {
                        totalPoints += Math.min(
                            Math.min(i, 9 - i),
                            Math.min(j, 9 - j))
                            + 1;
                    }
                }
            }
            System.out.println(totalPoints);
        }
        sc.close();
    }
}
```

## Problem 2 - [Princeton Cards](https://codeforces.com/group/hNnRWqFua0/contest/549922/problem/B)

This problem can be solved with sorting. If the array is sorted, then
all the repeated elements become consecutive elements in the array. So
one only needs to check one by one and count how many elements differ
from the previous one.

```java
import java.util.Arrays;
import java.util.Scanner;

public class PrincetonCards {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int N = sc.nextInt();
        int[] cards = new int[N];
        
        for (int i = 0; i < N; i++) {
            cards[i] = sc.nextInt();
        }
        
        Arrays.sort(cards);
        
        int uniqueCount = 1;  // There is at least 1 unique card (the first one)
        for (int i = 1; i < N; i++) {
            if (cards[i] != cards[i - 1]) {
                uniqueCount++;
            }
        }

        System.out.println(uniqueCount);
    }
}
```


## Problem 3 - [Biggest Island](https://codeforces.com/group/hNnRWqFua0/contest/549922/problem/C)

We can use a union find data structure (like a [weighted quick
union](https://algs4.cs.princeton.edu/15uf/WeightedQuickUnionUF.java.html))
to represent each cell of the grid. If we union any pair of adjacent
cells containing 1s, then each set in the union find data structure
will represent an island. Since the weighted quick union needs to keep
track of the size of each set, we can find the maximum value of its
size array to compute the answer.

Note that you can't use the algs4 library on codeforces, so you need
to re-implement the weighted quick union (but you can base your
implementation on the ones from 226 if you want to). We'll leave the
implementation up to you.