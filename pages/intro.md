---
permalink: /intro_guide
layout: page
---

{% include main_title.html text="Getting Started with Princeton Competitive Programming" %}

Competitive programming is an activity where individuals or teams
solve complex algorithmic and mathematical problems within strict time
limits. Participants use programming languages to devise efficient
solutions, aiming to optimize both correctness and speed.

In this guide you will learn the typical format of a problem, you will
learn how to approach problems, solve a problem and submit it to an
online judge, and finally learn how to understand time constraints.

Prerequisites: You should know how to program in some language and
know the basics of order of growth notation (namely big theta
notation).

## Problem Structure

A problem statement is usually divided into 6 sections:

1. **Problem Description**, the problem description provides the
context and defines the challenge. It explains the scenario or task
that needs to be solved. Sometimes, the description is stated in terms
of a story, and part of solving the problem requires interpreting this
story and "translating" it into a computer science/mathematical
problem.

2. **Input Format**, outlines the structure of the input data. It
describes how many lines of input there are, what kind of data you can
expect (integers, strings, etc.), and in what order the data is
provided.

3. **Constraints**, they specify properties of the input (like minimum
and maximum sizes) and thus they define how efficient your solution
has to be in order to solve the problem. This section is often part of
the input format section.

4. **Output Format**, specifies what the program should output after
processing the input. It's important that your solution follows this
format exactly, otherwise a correct solution could be misjudged as
incorrect.

5. **Sample Input/Output**, concrete examples of input data and the
corresponding expected output. These samples help you understand how
the input is structured and how the output should look. They can also
serve as basic test cases to verify your solution.

6. **Time/Memory Limits**, how long can your program run before it
terminates and outputs the solution, and how much memory it can use to
do so. Usually your programs should run in 1 to 5 seconds. This
section often comes in the very beginning of the problem.

After implementing a solution, you need to submit your code to the
online judge (more on this later), which automatically checks your
code against a series of test cases to ensure it works correctly.

Test cases are predefined sets of inputs that are run through your
code to validate its correctness and efficiency. When you submit your
code, it is executed using each input and your output is compared to
the correct one (hence why you need to follow the output format
exactly). You solve a problem if your program terminates within the
given time and memory limit for each test case and outputs the correct
answer.

When you submit your solution, it will be evaluated, and the outcome
will be categorized into one of the following:

- **Accepted (AC)**: Your solution is correct, and it passed all the test cases within the time and memory limits.
- **Wrong Answer (WA)**: Your code executed but produced incorrect results for one or more test cases.
- **Time Limit Exceeded (TLE)**: Your code took longer than the allowed time limit on one or more test cases. This means your algorithm is too slow and needs optimization.
- **Memory Limit Exceeded (MLE)**: Your solution used more memory than allowed. This usually happens when storing too much data.
- **Runtime Error (RE)**: Your program encountered an error during execution, such as division by zero, array out of bounds, or stack overflow.
- **Compilation Error (CE)**: Your code failed to compile, usually due to syntax errors or incorrect usage of the language.

## Example Problem 1

**Problem Statement:** Time limit: 1 second, Memory Limit: 256MB

Given an sequence $a$ of $n$ integers, find the sum of all elements in the sequence.

**Input Format:**
The first line contains an integer $n$ ($1 \leq n \leq 10^5$) - the number of integers in the sequence.

The second line contains $n$ integers separated by spaces - the
integers in the sequence. The value of a sequence elements is bounded by: $-10^6 \leq a_i \leq 10^6$.

**Output Format:**
The output should contain a single integer: the sum of the integers in the sequence.

**Sample Input:**
```
4
1 2 3 4
```

**Sample Output:**
```
10
```

### Programming a Solution

To solve the above problem, you need to write a program that reads any
input that satisfies the input format and constraints, and outputs the
right answer. You can use whatever language you prefer, Java, C++,
Python, Rust, Go, ... You can also use your favorite IDE to write a
solution to the problem, IntelliJ, VS Code, Emacs, ... And make sure
you know how to compile and run programs in your favorite language in
your favorite IDE. It's also recommended that you use the terminal to
compile and run your programs (read the first two section of these
[126 lecture
slides](https://www.cs.princeton.edu/courses/archive/fall24/cos126/static/lectures/15InputOutput.pdf)
for a refresher on this).

Since the algorithms courses at Princeton use Java, we will focus on
Java for the rest of this article, but like we said, use whatever you
want.

### Input/Output in Java

To solve the above problem we need to first learn how read the input
and output the answer. Your program should read from standard in and
print to standard out. You might be used to the 126/226 libraries
(introcs or algs4) to do this, unfortunately you won't be able to use
them here. So here is how to do input/output in Java without these
libraries:

```java
Scanner sc = new Scanner(System.in);
int n = sc.nextInt();
int[] a = new int[n];

for (int i = 0; i < n; i++) {
    a[i] = sc.nextInt();
}
```

The above code creates an object of type *Scanner*, which is very
similar to *StdIn*. We use `nextInt()` to read the next integer from
the input (ignoring any whitespaces). In the code above, we store the
input in an array of `int`.

To output something we can use the following method:

```java
System.out.println(result);
```

Here is a solution to the above problem:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
	int[] a = new int[n];
	for (int i = 0; i < n; i++) {
            a[i] = sc.nextInt();
        }

        int sum = 0;
        for (int i = 0; i < n; i++) {
            sum += a[i];
        }
        System.out.println(sum);
    }
}
```

This solution takes $\Theta(n)$ time, since it reads the input and
then iterates through each element once to sum it to a variable.

### Submitting the Solution:

Now that we wrote a solution, we should check if it is correct. To do
so, we are going to submit it to an online judge called
[codeforces](https://codeforces.com). Codeforces hosts a wide range of
problems and contests, allowing users to submit their solutions and
get instant feedback.

Before you can submit your solution, you should create an account (or
login if you have one already) by clicking on *Register* in the top
right corner and fill out the required details.

To make your life simple, we created a group on codeforces where
we store all of the content from the Princeton Competitive Programming
sessions. To join this group, go to the following
[link](https://codeforces.com/group/hNnRWqFua0/) and click on the
*join* button on the right in order to access the problems.

Now, here is the [link](https://codeforces.com/group/hNnRWqFua0/contest/549915/problem/A) to the above problem. Tip: the
"Group Contests" is annoying because it's really long, minimize it by
clicking on the arrow in the top right corner. Look at the panels on
the right, and scroll down to the one called "Submit?". Pick your
programming language from the dropdown and select the file containing
your solution. Click "submit" and that's it, you submitted your first
competitive programming solution!

You should eventually be redirected to a page with a table with your
submission. It might take a few seconds to run, but eventually you
will see a verdict. And... it's a *Wrong Answer* on test ??... What?
How could such a simple program have failed! (Note: if you translated
the above to a different language, e.g. Python, you probably got an
*Accepted* verdict).

It's time to debug our code and try to understand what went wrong. The
first thing we should do is reread the problem statement. Pay close
attention to the input constraints: $1 \leq n \leq 10^6$ and $-10^6
\leq a_i \leq 10^6$. Wait, if $n$ is $10^6$ the $a_i$ are all $10^6$,
then their sum is $10^{12}$, which is more than what we can represent
in an `int` variable (the maximum value of an `int` is around $2 \cdot
10^9$, memorize this number)! So if we replace `int sum = 0;` with
`long sum = 0;`, it should fix this issue. Try to resubmit and see if
you get the desired *Accepted*.

## Example Problem 2

**Problem Statement:** Time limit: 1 second, Memory Limit: 256MB

Given an sequence $a$ of $n$ non-negative integers, find the number of
pairs of integers that sum to an odd number. In other words, find the
number of indices $1 \leq i \leq n$ and $1 \leq j \leq n$ such that $i
\neq j$ and $a_i + a_j$ is odd.

**Input Format:**
The first line contains an integer $n$ ($1 \leq n \leq 10^6$) - the number of integers in the sequence.

The second line contains $n$ integers separated by spaces - the
integers in the sequence. The value of a sequence elements is bounded by: $0 \leq a_i \leq 10^9$.

**Output Format:**
The output should contain a single integer: the
number of pairs of elements that sum to an odd number.

**Sample Input:**
```
4
1 2 3 2
```

**Sample Output:**
```
4
```

**Sample Explanation:**
The following pairs of numbers sum to an odd number: $1$ and $2$ (the
first one), $1$ and $2$ (the first one), $1$ and $2$ (the second one),
$2$ and $3$, and $3$ and $2$.

## First Attempt

Here is a simple possible solution to the problem, which loops through
all possible pairs of elements of $a$ and determines which ones have
an odd sum (using the remainder operator `%` and checking if it is not
0).

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
	int[] a = new int[n];
	for (int i = 0; i < n; i++) {
            a[i] = sc.nextInt();
        }

	long result = 0;
	for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if ((a[i] + a[j]) % 2 != 0)
                    result++;
            }
        }
	
        System.out.println(result);
    }
}
```

You might right away guess that this solution won't be good enough,
but try to submit it anyways, here is the [link](https://codeforces.com/group/hNnRWqFua0/contest/549915/problem/B) to
the problem. You will get a *Time Limit Exceeded* verdict, which means
this solution is too slow.

## Second Attempt

So we know that we need a more efficient solution. The above solution
runs in $\Theta(n^2)$ time, since it looks at all pairs of elements
from the array. But how are you supposed to know that this is too
slow?

### Time Limits and Big Theta Notation

Time limits in competitive programming are often given in seconds. A
typical time limit is 1 second, which means your solution should
execute within that time.

Here's a rough guide for how many operations are allowed within a
1 second time limit:

| $n$              | Possible complexities                      |
|------------------|---------------------------------------------|
| $n \leq 10$      | $\Theta(n!)$, $\Theta(n^7)$, $\Theta(n^6)$  |
| $n \leq 20$      | $\Theta(2^n \cdot n)$, $\Theta(n^5)$        |
| $n \leq 80$      | $\Theta(n^4)$                               |
| $n \leq 400$     | $\Theta(n^3)$                               |
| $n \leq 7500$    | $\Theta(n^2)$                               |
| $n \leq 7 \cdot 10^4$ | $\Theta(n\sqrt{n})$                   |
| $n \leq 5 \cdot 10^5$ | $\Theta(n \log n)$                    |
| $n \leq 5 \cdot 10^6$ | $\Theta(n)$                           |
| $n \leq 10^{18}$ | $\Theta(\log^2 n)$, $\Theta(\log n)$, $\Theta(1)$ |

You can use these estimates to decide if an algorithm will meet the
time requirements. For example, for out previous solution of
$\Theta(n^2)$, since $n$ is up to $10^6$, it was bound to time out.

You don't have to memorize this guide right away, but you'll gradually
learn it as you apply it.

### A Linear Solution

Let's now improve the previous solution. They observation we need to
solve the previous problem in linear time is the following: in order
for two integers to sum to an odd number, they need to have different
parities. So instead of counting pairs of numbers, we can count the
number of even integers and the number of odd integers, and then
multiply them to get the answer.

Here is a way of implementing that (notice that we use `long` to avoid
the issue from the first example problem):

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
	int[] a = new int[n];
	for (int i = 0; i < n; i++) {
            a[i] = sc.nextInt();
        }

	long evens = 0;
	long odds = 0;
	for (int i = 0; i < n; i++) {
	    if (a[i] % 2 == 0)
		evens++;
	    else
		odds++;
        }
	
        System.out.println(odds * evens);
    }
}
```

Go ahead and submit it. You might be surprised to see that it's still
too slow!

### Faster Input in Java

The reason it is still too slow is because `Scanner`, the class we use
to read the input, is pretty slow. It's very easy to use `Scanner`,
but for problems with a lot of input (like this one) it is too
slow. So we can use a different class called `BufferedReader`, which
is faster. Unfortunately, this class is harder to use. For example, it
only lets us read a whole line as a string, we need to split it into
tokens and then convert them to integers in order to store them in an
integer array. We can use a class called `StringTokenizer` to do so,
it splits a string into tokens separated by white space, and then lets
us read each one using a `next()` method, similar to the way a
`Scanner` works. One last note, to use these classes we have to add a
`throws IOException` statement after the signature of the `main()`
method.

Here is a solution that uses these classes.

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
	int[] a = new int[n];

	StringTokenizer st = new StringTokenizer(br.readLine());
        for (int i = 0; i < n; i++) {
            a[i] = Integer.parseInt(st.nextToken());
        }

	long evens = 0;
	long odds = 0;
	for (int i = 0; i < n; i++) {
	    if (a[i] % 2 == 0)
		evens++;
	    else
		odds++;
        }
	
        System.out.println(odds * evens);
    }
}
```

Submit it. You should finally see the *Accepted* result.

## My Competitive Programming Journey

Now that you've learned your basics of competitive programming you'll
be able to enjoy the weekly sessions. Every week you'll have a few
problems of increasing difficulty. Some of them might have associated
readings that teach you some algorithm, data structure, or some
technique. You don't have to solve all the problems every week, just
solve one more than you knew how to solve before each session, that
way you'll be learning something new every week.