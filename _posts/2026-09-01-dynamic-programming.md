---
layout: post
title: Dynamic Programming For Dummies
date: 2026-09-01
description: A quick look into some basic dynamic programming approaches, exploring Fibonacci numbers.
tags: [dp-for-dummies, algorithms]
categories: [blog]
featured: true
---

If you read my earlier blog about my Secret Santa application, you might have been curious about the parallels to the Traveling Salesman Problem (TSP) but with the complete lack of any mention of dynamic programming. For such NP-hard problems, dynamic programming approaches can be great time savers. While true, there are a few key differences between the TSP and the Secret Santa Question:

- For one, in the Secret Santa Question (SSQ) we aren't trying to optimize path length (unlike the TSP). Though the shortest path through cities in the TSP will be a Hamiltonian Cycle, it is also the *shortest* Hamiltonian Cycle. Obviously, in the SSQ there's not really a "distance" element at all-- any Hamiltonian Cycle will suffice. 
- As a direct result of this previous point, the NP-hard nature of the TSP means in order to find the *shortest* path, we will need to somehow evaluate all the paths. But, in the SSQ we can stop once we find *any* old Hamiltonian Cycle. 

Because of these factors, I thought it unnecessary to apply true dynamic programming (DP) strategies and figured just applying the Depth First Search (DFS) would suffice. But, I also started to realize that the SSQ could actually be represented in a few ways (all of which can be approached using DP):

- Finding a Hamiltonian Cycle (or finding how many Hamiltonian Cycles) exist in a given graph
- Traveling Salesman
- Randomly assigning preferred objects (once we talk about this, you'll be able to complete [LeetCode 1434. Number of Ways to Wear Different Hats to Each Other](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/description/).)

First, I'd like to go over the basics of DP specifically:

- Recursion
- Memoization (Top-Down)
- Tabulation (Bottom-Up)
- Bitmasks