---
permalink: /fall24/week4_learn/solutions
layout: page
---

{% include main_title.html text="Fall 24 - Learn Division Week 4 - Solutions" %}

Problem set [link](https://codeforces.com/group/hNnRWqFua0/contest/555432).

## Problem A. New Netids

Since this was an implementation problem, here is a solution that uses
a `TreeMap`, which is a standard Java implementation of a balanced
binary search tree:

```java
import java.util.Scanner;
import java.util.TreeMap;

public class NewNetids {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int q = scanner.nextInt();
        scanner.nextLine(); // consume the newline character after the integer

        TreeMap<String, String> userDatabase = new TreeMap<>();

        for (int i = 0; i < q; i++) {
            String[] input = scanner.nextLine().split(" ");
            String operation = input[0];
            String netid = input[1];
            String password = input[2];

            if (operation.equals("ADD")) {
                userDatabase.put(netid, password);
            } else if (operation.equals("LOGIN")) {
                if (userDatabase.containsKey(netid) && userDatabase.get(netid).equals(password)) {
                    System.out.println("LOGGED IN");
                } else {
                    System.out.println("ACCESS DENIED");
                }
            }
        }
        scanner.close();
    }
}
```

## Problem B. Word Game

```java
import java.util.*;

public class WordGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt(); // number of test cases

        while (t-- > 0) {
            int n = scanner.nextInt(); // number of words for each player
            scanner.nextLine(); // consume newline

            String[] player1 = scanner.nextLine().split(" ");
            String[] player2 = scanner.nextLine().split(" ");
            String[] player3 = scanner.nextLine().split(" ");

            // Map to count word frequencies
            TreeMap<String, Integer> wordCount = new TreeMap<>();

            for (String word : player1) wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);
            for (String word : player2) wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);
            for (String word : player3) wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);

            int points1 = 0, points2 = 0, points3 = 0;

            // Calculate points for player 1
            for (String word : player1) {
                if (wordCount.get(word) == 1) points1 += 3;
                else if (wordCount.get(word) == 2) points1 += 1;
            }

            // Calculate points for player 2
            for (String word : player2) {
                if (wordCount.get(word) == 1) points2 += 3;
                else if (wordCount.get(word) == 2) points2 += 1;
            }

            // Calculate points for player 3
            for (String word : player3) {
                if (wordCount.get(word) == 1) points3 += 3;
                else if (wordCount.get(word) == 2) points3 += 1;
            }

            System.out.println(points1 + " " + points2 + " " + points3);
        }
        scanner.close();
    }
}
```

## Problem C. Restoring the Duration of Tasks 

To solve this problem you need to simulate the process mentioned in
the statement. Even though the problem is about a queue-like
simulation, you don't actually need to use a queue data
structure. Loop through the tasks and calculate when we actually
started to work on a task: either when the task arrived or when the
previous task was completed, whichever is greater.


```java
import java.util.Scanner;

public class PolycarpTasks {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();
        
        while (t-- > 0) {
            int n = scanner.nextInt();
            
            int[] s = new int[n];
            int[] f = new int[n];
            
            for (int i = 0; i < n; i++) {
                s[i] = scanner.nextInt();
            }
            
            for (int i = 0; i < n; i++) {
                f[i] = scanner.nextInt();
            }
            
            int lastFinishTime = 0;
            
            for (int i = 0; i < n; i++) {
                int startTime = Math.max(lastFinishTime, s[i]);
                int duration = f[i] - startTime;
                lastFinishTime = f[i];
                System.out.print(duration + " ");
            }
            System.out.println();
        }
        
        scanner.close();
    }
}
```

## Problem D. Social Network

Use a `LinkedList` (which is basically a stack) to represent the
conversations on the smartphone screen and a `TreeSet` (i.e. a
balanced search tree) to track the conversations currently
displayed. For each message, if the friend's ID is not already on the
screen, we check if the screen is full (i.e., it contains $k$
conversations). If it is full, the oldest conversation (last element)
is removed. Then, the new conversation is added to the front of the
list (top of the screen). By using the `TreeSet`, we ensure efficient
lookups to check whether a conversation is already on the
screen. Finally, the size of the list and its contents are printed in
the required order.

```java
import java.util.*;

public class SocialNetworkMessages {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        int n = scanner.nextInt(); // number of messages
        int k = scanner.nextInt(); // max conversations on screen
        
        LinkedList<Integer> screen = new LinkedList<>();
        TreeSet<Integer> onScreen = new TreeSet<>();
        
        for (int i = 0; i < n; i++) {
            int friendId = scanner.nextInt();
            
            // If the friendId is not already on the screen
            if (!onScreen.contains(friendId)) {
                // If the screen is full, remove the last conversation
                if (screen.size() == k) {
                    int removed = screen.removeLast();
                    onScreen.remove(removed);
                }
                // Add the new conversation to the top of the screen
                screen.addFirst(friendId);
                onScreen.add(friendId);
            }
        }
        
        System.out.println(screen.size());
        for (int id : screen) {
            System.out.print(id + " ");
        }
        System.out.println();
        
        scanner.close();
    }
}
```

## Problem E. Greg and Array

First, let's review the concept of difference arrays. Instead of
directly updating the values in the array over a specified range, we
use a difference array to store the increment or decrement at the
start and end of the range. The key idea is that for an update over
the range `[l, r]`, we increase the value at index `l` by a certain
amount and decrease the value at index `r+1`. After all updates are
recorded in the difference array, a single pass with prefix sums
(i.e., accumulations of sums of prefixes of the array) converts these
differences into actual values for the original array. This reduces
the time complexity of multiple range updates from $\Theta(nm)$ to
$\Theta(n + m)$, where $n$ is the size of the array and $m$ is the
number of operations.

In this problem, we need to use difference arrays twice. First, we use
a difference array `opCount` to track how many times each operation
should be applied based on the queries. For each query, instead of
directly applying multiple operations, we increment the start of the
operation range and decrement the end to signify how often each
operation should be applied. Then, another difference array effect is
used to efficiently apply the actual operations to the array. For each
operation, we record its effect over its range based on how many times
it should be applied, and finally, we compute the final result by
applying these effects cumulatively to the original array.