---
layout: post
title: 'Fun With Primes Numbers!'
date: 2026-11-05
description: Some facts notes about prime numbers from a Number Theory perspective that will be a useful reference in an upcoming project on RSA encryption!
tags: [number-theory, primes, encryption, rsa]
categories: [blog]
featured: true
marimo: true
related_posts: false
related_publications: true
---
## A few things to know before we get started...
Some prereqs...
- prime factorization
- modular arithmetic/ congruence

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
Therefore, we will **always** have a new prime to append to P. 

For example, we know that in iteration (5), our new prime factor $p_5 =13$ will not repeat because since $p|(2)(3)(7)(43)$ for $p\in\{2,3,7,43\}$, *none* of $\{2,3,7,43\}$ will divide $(2)(3)(7)(43) + 1$ (by Euclid's Proof of Infinite Primes). 

### Dirichlet's Theorem
A couple millennia after Euclid, in 1837 Peter Dirichlet proved a theorem that came to be known as Dirichlet's Theorem on Arithmetic Progressions, which states

> Let $a, \in \mathbb{Z}$ such that $gcd(a,m) = 1$. Then, $\exists$ infinitely many primes that are congruent to $a$ modulo $m$. That is, $\exists$ infinitely many primes $p\in\mathbb{N}$ such that

$$p \equiv a (\text{mod m})$$

The proof of this is very involved and is a lot more than we will get into here, but it is simple to see that is $gcd(a,m) > 1$ this theorem no longer holds. Let's choose $a = 35$ and $m = 77$. Clearly, $gcd(35, 77) = 7$. If there were infinitely primes $p\in\mathbb{N}$ such that $p \equiv 35 (\text{mod } 77)$, this implies that by the definition of congruence we should be able to generate those $p$ using the expression
$$ p = 77x + 35 = 7(11x +5)$$
where $x \in\mathbb{N}$. But, clearly the only prime this could possibly generate is $p=7(1)$, otherwise $7|p \implies$ p is composite, *not* prime. Moreover, $\not\exists x\in\mathbb{N}$ such that $11x + 5 = 1$ is true. So, we have found a counterexample where this theorem fails if $gcd(a,m) \not= 1$. 

Also, though very involved to prove Dirichlet's Theorem generally, we can prove it works pretty easily for specific chosen values of $a$ and $m$. For example, let $a = 3$ and $m = 4$. Clearly, $gcd(3,4) = 1$, so Dirichlet's Theorem applies. We can also prove that there exists infinitely many $p\in\mathbb{N}$ such that
$$p\equiv 3 (\text{mod }4)$$
**without Dirichlet's Theorem!** This actually looks pretty similar to Euclid's proof for infinitely many primes, but is also and example of Dirichlet's-- which is pretty cool!

We will show Dirichlet's holds in this case using contradiction. Assume $\exists$ a *finite* amount of primes $p\in\mathbb{N}$ such that $p\equiv 3 (\text{mod }4)$ denoted
$$P = \{p_0 = 3, p_1 = 7, \cdots, p_n\}$$
Now, we can define a number $m$ (note that $p_0 = 3$ is purposely omitted)
$$m = 4(p_1\cdots p_n) + 3$$
We have just forced it to be true that
$$m\equiv 3(\bmod 4)$$
Note that $\forall p_i \in P$, $p_i \not| m$ since it would need to be true that if $p_i|m$ and $p_i|4(p_1\cdots p_i \cdots p_n)$, then by the division theorem $p_i| [m - 4(p_1p_2\cdots p_n)] \implies p_i|3$. But, this isn't possible since we purposefully omitted $p_0=3$ from our definition of $m$, and hence $p_i > 3$. Therefore, (by another sub-contradiction) $p_i \not| m$. 
We also know that $m$ is odd because $\forall n\in\mathbb{N}$, $2|4n$ implies $4n$ is even. Then, adding 3 guarantees $4n+3$ will always be odd, and so will $m$. Therefore, the prime factors of $m$, which must come from the finite set $P$ are congruent to either 1 or 3 modulo 4. By construction, $m \equiv 3 (\text{mod }4)$. This means $m$ must have at least one prime factor $q \equiv 3 (\text{mod }4)$ (see the Multiplication Property of Modular Arithmetic). But, previously we showed that *none* of the finitely many primes in $P$ (which we have supposed to be all of those primes such that $p_i \equiv 3 (\text{mod }4)$) divide $m$. Therefore, there **must** exist a prime $p \equiv 3 (\text{mod }4)$ that is not in $P$! 

Therefore, we can conclude there are infinitely many primes $p$ such that $p \equiv 3 (\text{mod }4)$. 

Similarly to the previous prime generator, we have the algorithm:
1. $P = \{7\}$
2. $m = 4(7) + 3 = 31 \implies P=\{7,31\}$
3. $m = 4(7)(31) + 3 = 871 = 67(13) \implies P =\{7,13, 67\}$
4. $m = 4(7)(31)(67) + 3 = 58189 = 19(3061) \implies P =\{7,13,19, 67\}$

And so on and so forth!

## Does the Euclid-Mullin Sequence contain all the primes?
**Short answer:** We don't know!

**Long answer:** But there is generalization that does contain all the primes!

Clearly, the Euclid-Mullin Sequence doesn't generate the primes in order. Where we left off in our example of the algorithm, we had
$$P = \{2,3,7,13,43,..\}$$

It's plain to see some of the primes are missing-- at least missing up through iteration $5$-- like $5, 11, 17, 19$. But, we already saw in our example the primes are not generated in order from least to greatest since we generated 43 before 13. This begs the question: does the Euclid-Mullin Sequence generate *all* the primes eventually?

This question was posed originally by the titular Mullin in 1963, but still this question remains open. Generally, we can create variations of the Euclid-Mullin sequence by varying that *seed* we begin the construction with. The *seed* is the initial set $P$ we begin the algorithm with, $P = \{p_1, \cdots, p_k\}$. In the case on the typical Euclid-Mullin sequence, $P = \empty$, with the convention that the empty product is 1. Depending on the seed we start with, it is demonstrable that some Euclid-Mullin sequence variations *do not* contain all the primes {% cite booker2016varianteuclidmullinsequencecontaining %}.

Basically, it is not known if there is a single seed that generates all the primes. But, interestingly the previously cited {% reference booker2016varianteuclidmullinsequencecontaining %} proves the *generalized* Eucild construction *does* in fact generate all the primes. The generalized Euclid construction is as follows: 

{% quote booker2016varianteuclidmullinsequencecontaining %} [I]f $\{p_1,\cdots, p_k\}$ is a set of prime numbers, then for any $I \subseteq \{1,\cdots,k\}$, the number 
$$N_I = \prod_{i\in I} p_i + \prod_{i\in\{1,\cdots,k\}\backslash I}p_i$$

is coprime to $p_1 \cdots p_k$ and has at least one prime factor. Iteratively
choosing a set $I$ and a prime $p_{k+1} | N_I$, we obtain an infinite sequence $p1, p2, \cdots$ of distinct prime numbers, as in Euclid’s proof. (Note that Euclid’s construction is the special case in which $I = \emptyset$ at each step.)
We call a sequence resulting from this more general construction a generalized Euclid sequence with seed $\{p_1,\cdots, p_k\}$. {% endquote %}

That's pretty complicated, and computationally dense-- but it is a cool result that a variation of the Euclid-Mullin Sequence is proven to generate all the primes.

## Some other functions known to generate all the primes
[Formula for primes](https://en.wikipedia.org/wiki/Formula_for_primes)

# Is Number Theory Useful?
**Short answer:** Some of it!

**Long answer:** Yes! Cryptography is field in which it is pretty useful. But, does number theory need to be useful to make it worth studying?

