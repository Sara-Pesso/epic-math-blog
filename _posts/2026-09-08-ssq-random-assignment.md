---
layout: post
title: 'Dynamic Programming For Dummies - Pt. 3: SSQ as an Assignment Problem'
date: 2026-09-08
description: How to solve SSQ like a Random Assignment problem using DP and bitmasking. 
tags: [dp-for-dummies, algorithms, comp-sci, random-assignment, SSQ]
categories: [blog]
featured: true
marimo: true
---

## Introduction

So, if you'll recall from the [first blog post](https://sara-pesso.github.io/epic-math-blog/blog/2026/dynamic-programming/) in this series, we are going to explore three different dynamic programming solutions for the Secret Santa Question (SSQ):

- Finding a Hamiltonian Cycle (or finding how many Hamiltonian Cycles) exist in a given graph
- Traveling Salesman
- Randomly assigning preferred objects (once we talk about this, you'll be able to complete [LeetCode 1434. Number of Ways to Wear Different Hats to Each Other](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/description/).)

We're going to start with treating the SSQ as a Random Assignment Problem. In the original [SSQ blog post]() I talked about how randomly assigning Secret Santa participants to each other and then checking whether those pairings were allowed based on the user inputted exclusions was my first attempt at tackling this problem on behalf of my MIL. Because of that, I think updating the original revision made in that post (i.e., implementing Depth-First Search (DFS) in order to find a Hamiltonian Cycle) with memoization would be an appropriate way to begin.

To be clear, while we are once again implementing DFS we are not necessarily interested in finding a *Hamiltonian Cycle*. All we want is *any* valid assignment of gift-givers and gift-receivers. I think leaving out the Hamiltonian Cycle aspect of the SSQ for our first foray into solving it using DP will make the explanations more simple and therefore digestible. 

But: fret not! We will also look at a DP way to solve the SSQ in a later post! 

## Randomly Assigning Objects to Nodes

The analogous LeetCode problem (1434) of this heuristic is about assigning hats to people. Ours is about assigning gift-givers to gift-getters. To make this as generic as possible-- just in case you're here to solve a different analogous problem-- will be to assign **objects** to **nodes**. 

In this heuristic, the goal is to assign each of $n$ nodes a corresponding object, based on whether that node is allowed to be assigned the object. Obviously, we need at least $n$ objects to assign, but we can have more than $n$ objects-- with the caveat that not every object will be assigned. Of course, in the Secret Santa case the number of objects ("gift-getters") is the same as the number of nodes ("gift-givers"). The index of each object every node is allowed to be assigned is held in it's own list. In Python, the allowable assignments will be stored in a list of lists of length $n$, where for $0 < i <  n$, the $i^{th}$ list represents those objects' indices allowed to be assigned to the $i^{th}$ node. 

For example:
```python
objs = [[0, 1, 2], 
        [2, 3], 
        [0, 1], 
        [3, 4]]
```
In this example, node (gift-giver) 2 can only be assigned object (gift-getter) 0 or 1. (Note: Recall that Python iterates from 0! This means the maximum object index is 1 less than $n$, the total number of objects). 

### Tabulation
OK!-- it's now time for the big reveal: how we can use the tabulation and bitmask example from the [previous post]() in this series to solve the SSQ!

Recall that in that example we used DP in tabulation to minimize the *cost* of assigning each object to a person-- giving us a very specific assignment arrangement. The easiest way to use this to solve the SSQ: simple edit the cost matrix to (negative) binary!

Normally, we'd be inclined to codify our matrix as follows:
- if person $i$ is allowed to be assigned person $j$ as their gift-giver in SSQ, in the cost matrix, set $C_{ij} = 1$
- if that combination is *not* allowable, set $C_{ij} = 0$.

This might seem like it work, but the algorithm is optimizing for *minimum* cost; it would favor picking the 0-entries (which it's not allowed to do!). So, instead codify it like this:

Normally, we'd be inclined to codify our matrix as follows:
- if person $i$ is allowed to be assigned person $j$ as their gift-giver in SSQ, in the cost matrix, set $C_{ij} = -1$
- if that combination is *not* allowable, set $C_{ij} = 0$.

By setting allowed giver-getter combinations to -1, the algorithm will naturally favor picking a -1. Assuming there is at least one permutation of giver-getters possible, picking all -1s (allowed assignments) will naturally be the minimum. So, this is actually all we need to do in this case! No changes to the algorithm necessary!

For example, using the same script from that previous post, look at this example and output:
```python
## This example would be an easy way to use this for a Secret Santa problem!
costs = [
    [0, -1, -1],
    [-1 , 0, 0],
    [0, -1, 0]
]
```
Output:
```python
Node 0 -> Object 2: Cost -1
Node 1 -> Object 0: Cost -1
Node 2 -> Object 1: Cost -1
Min. Cost: -3
```
As you can see, each person ("node") is assigned to another Secret Santa participant ("object") to purchase a Christmas gift for whose cost is set to -1-- and the resultant minimum cost will always be $-n$ using this heuristic. 

This full script can be found on [my GitHub, here]().

### Memoization
In the LeetCode version of this problem, they just want to know how many **unique ways** there are to assign people 40 hats (40 being the max, because bitmasking is not appropriate for large $n$, see the [previous blog post on bitmasking]()). We will need to take this one step further: we need actually want to *display* one of those unique assignments. So, bearing this in mind we will write a counter function to solve this for LeetCode, then return the DP table, and finally write another function to extract any unique assignment from the DP table.

