---
layout: post
title: 'Dynamic Programming For Dummies - Pt. 3: SSQ with Memoization'
date: 2026-09-08
description: How to solve SSQ like a Random Assignment problem using DP, memoization, and bitmasking. 
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
