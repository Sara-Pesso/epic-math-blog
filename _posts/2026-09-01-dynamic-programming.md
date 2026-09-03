---
layout: post
title: Dynamic Programming For Dummies
date: 2026-09-01
description: A quick look into some basic dynamic programming approaches, exploring Fibonacci numbers.
tags: [dp-for-dummies, algorithms]
categories: [blog]
featured: true
marimo: true
---
## Introduction

If you read my earlier blog about my Secret Santa application, you might have been curious about the parallels to the Traveling Salesman Problem (TSP) but with the complete lack of any mention of dynamic programming. For such NP-hard problems, dynamic programming approaches can be great time savers. While true, there are a few key differences between the TSP and the Secret Santa Question:

- For one, in the Secret Santa Question (SSQ) we aren't trying to optimize path length (unlike the TSP). Though the shortest path through cities in the TSP will be a Hamiltonian Cycle, it is also the *shortest* Hamiltonian Cycle. Obviously, in the SSQ there's not really a "distance" element at all-- any Hamiltonian Cycle will suffice. 
- As a direct result of this previous point, the NP-hard nature of the TSP means in order to find the *shortest* path, we will need to somehow evaluate all the paths. But, in the SSQ we can stop once we find *any* old Hamiltonian Cycle. 

Because of these factors, I thought it unnecessary to apply true dynamic programming (DP) strategies and figured just applying the Depth First Search (DFS) would suffice. But, I also started to realize that the SSQ could actually be represented in a few ways (all of which can be approached using DP):

- Finding a Hamiltonian Cycle (or finding how many Hamiltonian Cycles) exist in a given graph
- Traveling Salesman
- Randomly assigning preferred objects (once we talk about this, you'll be able to complete [LeetCode 1434. Number of Ways to Wear Different Hats to Each Other](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/description/).)

First, I'd like to go over the basics of DP specifically:

- Recursion (Naive)
- Memoization (Top-Down)
- Tabulation (Bottom-Up)
- Bitmasks (see [this blog post](That's where DP can become a very useful tool--) for how this works!)

Let's jump into it by exploring the Fibonacci sequence!

## Fibonacci Sequence
A quick overveiw of what the Fibonacci sequence is; from Wikipedia: 
> In mathematics, the Fibonacci sequence is a sequence in which each element is the sum of the two elements that precede it.
So, starting with the smallest two natural numbers (that is the positive reals, denoted $\mathbb{N}$)

$$F = \{0,1,1,2,3,5,8,13,21, 34\dots\}$$

Is there an easy way to calculate the $n^{th}$ Fibonacci number? For large numbers, we don't want to manually do that many calculations. Even on a computer, calculating say, the $4,000,000^{th}$ Fibonacci number can be costly in both time and space. That's where DP can become a very useful tool. 

## Recursion (Naive)
This is the most basic way of solving dynamic programming problems, and by itself is **not** dynamic programming (but, the two DP big-dogs, memoization and tabulation, are both heavily on it, so we'll discuss it here). It is one of the core programming techniques and is worth understanding. 

There are two main parts to recursion:
1. **The Basis** (or Base Case): it is the simplest, smallest subproblem. In the Fibonacci sequence, which from here on out we will denote with $F(n)$ being the $n^{th}$ Fibonacci number (we will be working in Python, and therefore iterating from $0$). Therefore, $F(0) = 0$ is the basis (practically, $F(1)$ = 1 is the basis since adding $F(0)=0$ to any $F(i)$ doesn't change it). **Note that $F(n) = F(n-1) + F(n-1)$.**

In programming, the basis is also the stopping condition. Recursion otherwise would be an infinite loop, so knowing when to break out of the loop is key.

2. **Recursive Case**: This is simply $F(i), \forall i > 1$. That is, all the other Fibonacci numbers. 

We can divide the cases this way, because $\forall i > 1$, $F(i)$ is a repeated sum of $F(1)$. Let's take a look at $F(5)$. We know $F(5) = F(4) + F(3)$. We also know that $F(4) = F(3) + F(2)$, and $F(3) = F(2) + F(1)$, and so on and so forth. We can summarize this in a graph:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dp-blog/fib-recursion-tree.png" class="img-fluid w-70 rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visualization of calculating $F(5)$ using a graph.
</div>

We can see here how every branch of the tree eventually gets down to the $F(0)$ and $F(1)$ basis. Your computer handles this by going down a **callstack** in the *Forward Phase*, which keeps track of every subproblem in the recursion, all the way to basis on the branch, Then, upon reaching the basis, the recursive program knows to terminate (because we've told it to) and will move on to "going down" the next branch, until every subproblem has been fully solved. 

Once the Forward Phase is complete, the *Unwinding Phase* begins. This is the computer "coming back up" the callstack,and solving all the functions it's created (in the case of the Fibonacci sequence, basically this would look like a summation of a bunch of 1s, depending on the $n^{th}$ Fibonacci number we are calculating). The program then terminates, returning the $n^{th}$ Fibonacci number as the user defined. 

In Python, that would look something like this:

<div class="al-marimo-inline" markdown="1">

```python
def kthFibonacci_Recursion(n):
    
    # basis and termination criteria
    if n <= 1:
        return n
      
    # sum of the two preceding Fibonacci numbers: F(n) = F(n-1) + F(n-2)
    return kthFibonacci_Recursion(n - 1) + kthFibonacci_Recursion(n - 2)

print(kthFibonacci_Recursion(5))
```

</div>

As we can see, in the case of calculating Fibonacci numbers because each function call, $F(n)$, leads to the function being recursively called twice more, $F(n-1)$ and $F(n-2)$. This means we are calling the function $2^n$ times, and therefore the recursive solution has time complexity of $O(2^n)$. For the uninitiated to Big-O notation, this is not particularly good and means that, though a valid way to find the solution, it is a pretty slow algorithm.

But, like all things in life, there is a trade off. Space complexity is determined by the depth of just the *callstack* at it's deepest point. Looking at te $F(5)$ tree and counting the longest branch, we can see there are 5 function calls. In fact, this is true generally for the recursive solution to the Fibonacci calculation: the storage complexity is only $O(n)$. This isn't too bad! We don't need very much memory at all for this function, the trade off being we are only getting $F(n)$-- all the subproblem calculations for $F(i), \forall 0 < i < n$ are lost once the function call terminates. 

Next, we'll look at some ways to improve the time complexity, with some trade offs in terms of storage complexity because they store the results of the subproblems, too. 

## Memoization (Top-Down)

You can probably already see some redundancies in calculations looking at the $F(5)$ tree calculations. When we use recursions, we are calculating $F(3)$ twice, and every time we calculate $F(3)$, we calculate $F(2)$ once and $F(1)$ twice, and so on and so forth. 

What if we were able to save the results of these subproblems, instead of recalculating them repeatedly?

Doing this from the top-down--  that is, in Fibonacci terms, starting with $F(n)$ and working down the tree to $F(1)$-- and caches the results of each subproblem in a table to be pulled from later if the subproblem is revisited in a recursive algorithm (like Fibonacci numbers), is called **memoization**. Frequently such a table is referred to as a *memoization table* or *DP (dynamic programming) table*. Looking at the pseudocode for this, we'd have something like

1. Initialize the DP table (an empty $1xn$ vector). Where, $n$ is Fibonacci index of interest and NaN is a value that indicates the table hasn't yet been filled for a specific index:
$$dp = [NaN]^{1 x n}$$
2. Create the basis and termination criteria. This is the same as in the recursive approach: if we recurse to $n \leq 1$, begin working back up the callstack. 
3. Check the DP table for the result of the subproblem
    - if the subproblem has been solved before and we have the result (i.e.,$dp(i) \not = NaN$), return that value.
    - if the subproblem has not been solved before (i.e., $dp[i] = NaN$), continue solving via recursion until we hit a solved subproblem (or the basis), then save in the DP table and return the result. 

In Python,

<div class="al-marimo-inline" markdown="1">

```python
from math import nan

def kthFibonacciNumber_Memoization(k):
    dp = [nan] * (k + 1)

    def kthFibonacciUtil_Memoization(k, dp):
        # Basis: k <= 1 
        if k <=1: 
            return k

        # Case k > 1
        if dp[k] is not nan:
            # if we've already calculated/stored the kth fibonacci number
            return dp[k]

        # if we have NOT already calculated/stored the kth fibonacci number
        dp[k] = kthFibonacciUtil_Memoization(k - 1, dp) + kthFibonacciUtil_Memoization(k - 2, dp)

        return dp[k]
    return kthFibonacciUtil_Memoization(k, dp)

print(kthFibonacciNumber_Memoization(7))
```

</div>

So, the basic idea here isr we save on time complexity. For long recursive problems, say calculating $F(1,000,000)$, this is an important trade off to make as it will drastically decrease the time your algorithm needs to run. 

In terms of Big-O notation, we have reduced the time complexity from $O(2^n)$ (calling our function $2^n$ times), to only $O(n)$. This is because instead of repeatedly calculating the same subproblem over and over, we only need to calculate each subproblem once-- the rest of the time is a quick call to the DP table-- and there are only $n$ subproblems that need to be solved.

Of course, unlike pure recursion that doesn't store the results of any subproblem, it seems natural that memoization will require higher space complexity. But, this isn't actually the case. The **cache size** (the size of the DP table) is only $n$. Also, the resultant callstack is only (at most) $n$ calls deep. Therefore, 

$$O(n) + O(n) = O(n)$$

In actuality, even though it may seem like we are using more storage, this isn't really the case. Yet another reason dynamic programming is preferred to pure recursion.

## Tabulation (Bottom-Up)

The final dynamic programming method we will discuss in here, **tabulation**, works very similarly to memoization. The main difference is, tabulation is *Bottom-Up*, rather than memoization which is top-down. 

All this means is that instead of starting with our desired $F(n)$ and working down to the basis, $F(1)$, we instead start at the basis and calculate all the intermediate subproblems up to $F(n)$. That is to say, it is completely iterative. 

This actually probably the

The steps are similar to memoization:

1. Initialize the DP table (an empty $1xn$ vector). Where, $n$ is Fibonacci index of interest and NaN is a value that indicates the table hasn't yet been filled for a specific index:
$$dp = [NaN]^{1 x n}$$

2. Iterate through cases $i = 2$ to $i=n$, calculating each subproblem and filling in the DP table.

As a Python function, this looks like

<div class="al-marimo-inline" markdown="1">

```python
from math import nan

def kthFibonacciNumber_Tabulation(k):
    # Initialize the Fibonacci Numbers: [0,1]
    if k <= 1:
        return k

    dp = [nan] * (k + 1)
    dp[0], dp[1] = 0, 1

    # Solve up to k
    for i in range(2, k + 1):
        dp[i] = dp[i-1] + dp[i-2]

    return dp[k]

print(kthFibonacciNumber_Tabulation(7))
```

</div>

This particular implementation of tabulation for the Fibonacci sequence actually has the same time complexity and the same space complexity as memoization. Because each Fibonacci number is only calculated once and then the result is stored in the DP table, the time complexity remains as $O(n)$. The same is true of the space complexity, which remains as $O(n)$ as each number is catalogued in the DP table.

There is more than one way to skin a cat: we can implement tabulation slightly differently to improve the time complexity of the Fibonacci sequence. 

## Space Optimized Tabulation for the Fibonacci Sequence

Again, we can make a trade off. Recall,

$$F(n) = F(n-1) + F(n-2)$$

If we only care about finding $F(n)$ and we don't care about the results of all the subproblems, then we can simply "throw away" all the subproblems results, $F(i)$, $\forall i <  n-2$. In other words, we need only keep $F(i-1)$ and $F(i-2)$ at each iterative step, rewriting the same bit of memory each time. This way, we only ever have two of the Fibonacci numbers stored. 

In this case, the time complexity remains $O(n)$, since we are still calculating each Fibonacci number once, but the space complexity is reduced to $O(1)$, since we are only keeping track of two Fibonacci numbers at a time. 

That implementation is very similar:
1. Initialize the array $[F(i-2), F(i-1)] = [F(0), F(1)] = [0,1]$
2. For each $0 < i <n$:
    - Calculated $F(i) = F(i-1) + F(i-2)$
    - Update the array, where $F(i-1)$ becomes $F(i-2)$, and $F(i)$ becomes $F(i-1)$ before looping to the next $i^{th}$ Fibonacci number.

And as some executable Python, it looks like this:

<div class="al-marimo-inline" markdown="1">

```python
def kthFibTabulation_OptimizedSpace(k):
    if k <= 1: 
        return k

    # Store only the current Fibonacci number, instead of all k Fibonacci numbers
    current_fib = 0 

    # Initialize the first two Fibonacci numbers: [0,1]
    previous_fibs = [0,1]

    for _ in range(2, k + 1):
        current_fib = previous_fibs[0] + previous_fibs[1]

        #Update!
        previous_fibs = [previous_fibs[1], current_fib]

    return current_fib

print(kthFibTabulation_OptimizedSpace(7))
```
</div>

## Quick Time Comparison of the Dynamic Programming Methods!

This is a simple way to test and compare the speed of your algorithms in Python. The timeit library will run your algorithm $x$ times (in this case, 100,000 times) for whatever $F(k)$ we want. Choosing a larger $k$, like 100, is a good test because it becomes very computationally dense, as we can see if we think back to how large just the $F(5)$ tree was earlier. The timeit package then spits out how long (seconds) the all $x$ runs took, so if we divide by $x$ we get the average run time for each program.

In fact, recursion was so slow, it was omitted from this test. Feel free to un-comment it and see for yourself!

<div class="al-marimo-inline" markdown="1">

```python
import timeit
from memoization import total_time_memoization
from tabulation import kthFibonacciNumber_Tabulation, kthFibTabulation_OptimizedSpace
from recursion import kthFibonacci_Recursion

# Testing the time complexity
k = 100
runs = 100000

# total_time_recursion = timeit.timeit('kthFibonacci_Recursion(k)', globals=globals(), number=runs)
# print(f"Average Recursion Time: {total_time_recursion/runs:.7f} seconds")

total_time_memoization = timeit.timeit('kthFibonacciNumber_Memoization(k)', globals=globals(), number=runs)
print(f"Average Memoization (Top-Down) Time: {total_time_memoization/runs:.7f} seconds")

total_time_tabulation = timeit.timeit('kthFibonacciNumber_Tabulation(k)', globals=globals(), number=runs)
print(f"Average Tabulation (Bottom-Up) Time: {total_time_tabulation/runs:.7f} seconds")

total_time_tabulation_opt = timeit.timeit('kthFibTabulation_OptimizedSpace(k)', globals=globals(), number=runs)
print(f"Average Tabulation Optimized (Bottom-Up) Time: {total_time_tabulation_opt/runs:.7f} seconds")
```
</div>

This test script's results vary slightly between runs, but in general you will see that memoization is clearly the slower method, with the two implementations of tabulation significantly faster, but neck and neck with each other. This makes sense given our discussions about the time complexity of these methods, with respect to the Fibonacci sequence. 

## Conclusion

As aforementioned in our discussion about recursion, having our tabulation algorithm space optimized isn't always going to be a positive. In the case of the Fibonacci sequence, it probably doesn't really matter what any of the answers to the subproblems were, so it's fine if we simply delete them. But, some of the other famous problems we talked about earlier would not fair as well when we sacrifice space complexity. 

For example, if we were to use such a method when trying to solve TSP, if we didn't keep track of *all* the cities and the order we visited them in, we might be able to spit out the minimum distance our salesman can possibly travel, but we would not have saved the route he needs to take. Same goes for the SSQ or LeetCode 1434-- maybe we could quickly determine that there does in fact exist some solution, but we won't be able to show it at the end of the algorithm. We will be exploring all of these in subsequent blog posts, but just something to chew on for now.

There is another really important way we can improve the time and space complexity of our dynamic programming algorithms: The Bitmask. Bitmasks are essentially using the binary representation of natural numbers to represent various subproblem states. This primarily improves space complexity, but will also help with speed. And it's crucial if we want efficient algorithms that also give us the route our salesman need to take! For a crash course on Bitmasks, see the next blog post in this series [here](https://sara-pesso.github.io/epic-math-blog/blog/2026/bitmasks/). 

Hopefully this crash course on dynamic programming was pretty easy to understand and digest, because we are only going to build from here! Please see my [GitHub Repo]() for the code used in this post!

- Sara 9/1/2026