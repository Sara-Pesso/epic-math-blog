---
layout: post
title: Dynamic Programming For Dummies
date: 2026-09-01
description: A quick look into some basic dynamic programming approaches, exploring Fibonacci numbers.
tags: [dp-for-dummies, algorithms]
categories: [blog]
featured: true
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
        {% include figure.liquid loading="eager" path="assets/img/dp-blog/fib-recursion-tree.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visualization of calculating $F(5)$ using a graph.
</div>

## Memoization (Top-Down)

## Tabulation (Bottom-Up)