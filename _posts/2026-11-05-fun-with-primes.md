---
layout: post
title: 'Fun With Primes'
date: 2026-11-05
description: Some facts notes about prime numbers from a Number Theory perspective that will be a useful reference in an upcoming project on RSA encryption!
tags: [number-theory, primes, encryption, rsa]
categories: [blog]
featured: true
marimo: true
---

# Fun with Prime Numbers!
- prime factorization
## Are there infinite prime numbers?
**Short answer:** YES!!

**Long answer:** YES!! We have known this since before Christ, in fact!
Sometime around 300 B.C. Euclid figured this out using a clever contradiction. 

### Euclid's Proof of Infinite Primes
Suppose there are a finite amount of prime natural numbers, then there should be a maximum prime. We can define the set of $n$ primes as
$$P = \{p \in \mathbb{N}: \text{p is prime}\}= \{p_1,p_2,...,p_n\}$$
Again, there only $n$ primes:
$$|P| = n$$

As aforementioned, prime factorization tells us that $\forall x \in \mathbb{N}$, $x$ can be written as a product of prime factors. Thus, because there are only $n$ primes in $P$, $x$ can be written as the product of $p_1,p_2, ..., p_n$. 

Consider the natural number
$$m = \prod_{i = 1}^{n}p_i + 1 = (p_1p_2\cdots p_n) + 1$$
Let us define
$$b :=  \prod_{i = 1}^{n}p_i$$
So, we can rewrite $m$ as
$$m = b + 1$$
<!-- Note that because $x > 0$, $\forall x \in \mathbb{N}$
$$m \ge p_1 + 1 \ge 2+1$$
$$m \ge 3$$ -->

Is $m$ prime? Suppose it is not prime (such a number is called *composite*), then because there are finitely many primes in $P$, $m$ would have a prime factorization consisting of at least one $p_i$, where $i\in[1,n]$. In other words, if $m$ is prime $\exists p_i$, where $i\in[1,n]$ such that $\frac{m}{p_i}\in\mathbb{N}$, or simply
$$p_i |m$$

Of course, we also have 
$$p_i | (p_1p_2\cdots p_{i-1}p_i p_{i+1}\cdots p_n)\implies p_i| b$$

Then, by the Division Theorem, it must also be true that
$$p_i|(m - b)$$
So, 
$$p_i | ((b+1) - b) \implies p_i| 1$$
Clearly, this is a contradiction! 
So, $\not \exists p_i \in P$ such that $p_i|m$. This means, that either
- $m$ itself is prime, but $m \not\in P$
- $m$ is divisible by a prime factor not in $P$
Either way, there are primes that are *not* in $P$! Therefore, there must exist infinite primes. (Think about it this way, we could add $m$ to $P$ and then repeat this process again, and then do it again, and again, and again-- indefinitely!)


## Can we generate primes?
**Short answer:** YES!!

**Long answer:** YES!! There are known functions that can generate every prime number in order-- but they have some computational issues when trying to find the $n^{th}$ prime for very large values of $n$.

We can actually use Euclid's proof of infinite primes to make an algorithm to generate primes, because as previously stated either
- $m$ is a new prime itself
- or $m$ has a new prime factor
This sequence is known as the Euclid-Mullin sequence. 
### Euclid's Prime Algorithm (Euclid-Mullin Sequence)
1. Start with the smallest prime: $P = \{2\}$
2. $m = 2 +1 = 3$, 3 is prime $\implies P=\{2,3\}$
3. $m = (2)(3) + 1$, 7 is prime $\implies P=\{2,3,7\}$
4. $m = (2)(3)(7) + 1 = 43$, 43 is prime $\implies P = \{2,3,7,43\}$
5. $m = (2)(3)(7)(43) + 1 = 1807 = (139)(13)$, 13 and 139 are prime $P = \{2,3,7,13,43\}$
(NOTE: 139 is also prime, but we only add the smaller of the two new prime factors-- so, in this case only 13 is added!)

We can be sure the new primes and prime factors we find each iteration will not repeat in subsequent iterations of this algorithm because if for iteration $n$ when we find new prime $p_n$, because all the subsequent 
$$p_i\Biggl|\prod_{i=1}^{n-1}p_i, \text{ }\forall i \in[1,n-1]$$
we can be sure each $p_i$, $\forall i \in[1, n-1]$
$$p_i \not \Biggl| \Biggl[\prod_{i=1}^{n-1}p_i\Biggr] +1$$
Therefore, we will **always** have a new prime to append to $P$. 

For example, we know that that in iteration (5), our new prime factor $p_5 =13$ will not repeat because since $p|(2)(3)(7)(43)$ for $p\in\{2,3,7,43\}$, *none* of $\{2,3,7,43\}$ will divide $(2)(3)(7)(43) + 1$ (by Euclid's Proof of Infinite Primes). 

## Does the Euclid-Mullin Sequence contain all the primes?
**Short answer:** No!

**Long answer:** But there are variations that can!

[A VARIANT OF THE EUCLID–MULLIN SEQUENCE CONTAINING
EVERY PRIME](https://arxiv.org/pdf/1605.08929)



# Is Number Theory Useful?
Short answer: Some of it!
Long answer: Does it need to be?

