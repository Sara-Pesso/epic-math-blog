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
toc:
  sidebar: left
---
# Introduction from Yours Truly
This semester, I've had the privilege to take a graduate level course in Number Theory as I work towards my MS. As someone who enjoys puzzles and solving problems, such a proofs based class has been pretty fun. I've heard criticisms about Number Theory previously: how it's not applicable or useful to anything in the real world. Generally, I think this misses the point of study pure mathematics. Not to mention it's up to people to *find* or create a way to use this stuff productively. 

This post is going to serve mostly as an introduction to the primes. I want to go into detail about how 
1. There are infinitely many primes
2. Even though do have ways to generate all the primes, these methods are extremely inefficient

And then how these two points give motivation to RSA encryption algorithm. An in-depth explanation and implementation of RSA will be [in a future post!](https://sara-pesso.github.io/epic-math-blog/blog/2026/RSA/)

## A few things to know before we get started...
I am not going to go into detail about the basic number theory, just some of the more advanced topics. Some prerequisite topics to understand that will make this post more palatable are:
- Prime factorization
- Modular arithmetic
- Congruence and the Division Theorem
- Cardinality

If you understand how these work, understanding this post should be a cake walk!

# Are there infinite prime numbers?
**Short answer:** YES!!

**Long answer:** YES!! We have known this since before Christ, in fact!
Sometime around 300 B.C. Euclid figured this out using a clever contradiction. 

## Euclid's Proof of Infinite Primes
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
<br>
<br>
So, $\not \exists p_i \in P$ such that $p_i|m$. This means, that either
- $m$ itself is prime, but $m \not\in P$
- $m$ is divisible by a prime factor not in $P$
Either way, there are primes that are *not* in $P$! Therefore, there must exist infinite primes. (Think about it this way, we could add $m$ to $P$ and then repeat this process again, and then do it again, and again, and again-- indefinitely!)


# Can we generate primes?
**Short answer:** YES!!

**Long answer:** YES!! There are known functions that can generate every prime number in order-- but they have some computational issues when trying to find the $n^{th}$ prime for very large values of $n$.

We can actually use Euclid's proof of infinite primes to make an algorithm to generate primes, because as previously stated either
- $m$ is a new prime itself
- or $m$ has a new prime factor
This sequence is known as the Euclid-Mullin sequence. 

## Euclid's Prime Algorithm (Euclid-Mullin Sequence)
Adapted from {% reference silverman2012friendly %}:

1. Start with the empty set: $P = \{0\}$
2. $m = 1+1 = 2 \implies P =\{2\}$ (by convention, the empty set product is 1).
3. $m = 2 +1 = 3$, 3 is prime $\implies P=\{2,3\}$
4. $m = (2)(3) + 1$, 7 is prime $\implies P=\{2,3,7\}$
5. $m = (2)(3)(7) + 1 = 43$, 43 is prime $\implies P = \{2,3,7,43\}$
6. $m = (2)(3)(7)(43) + 1 = 1807 = (139)(13)$, 13 and 139 are prime $P = \{2,3,7,13,43\}$
(NOTE: 139 is also prime, but we only add the smaller of the two new prime factors-- so, in this case only 13 is added!)

We can be sure the new primes and prime factors we find each iteration will not repeat in subsequent iterations of this algorithm because if for iteration $n$ when we find new prime $p_n$, because all the subsequent 
$$p_i\Biggl|\prod_{i=1}^{n-1}p_i, \text{ }\forall i \in[1,n-1]$$
we can be sure each $p_i$, $\forall i \in[1, n-1]$

$$p_i \not \Biggl| \Biggl[\prod_{i=1}^{n-1}p_i\Biggr] +1$$

Therefore, we will **always** have a new prime to append to $P$.
<br>
<br>
For example, we know that in iteration (5), our new prime factor $p_5 =13$ will not repeat because since $p|(2)(3)(7)(43)$ for $p\in\{2,3,7,43\}$, *none* of $\{2,3,7,43\}$ will divide $(2)(3)(7)(43) + 1$ (by Euclid's Proof of Infinite Primes). 

## Dirichlet's Theorem
A couple millennia after Euclid, in 1837 Peter Dirichlet proved a theorem that came to be known as Dirichlet's Theorem on Arithmetic Progressions, which states

> Let $a, \in \mathbb{Z}$ such that $gcd(a,m) = 1$. Then, $\exists$ infinitely many primes that are congruent to $a$ modulo $m$. That is, $\exists$ infinitely many primes $p\in\mathbb{N}$ such that

$$p \equiv a (\text{mod m})$$

{% cite silverman2012friendly %}

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

We have just forced it to be true that $m\equiv 3(\bmod 4)$.

Note that $\forall p_i \in P$, $p_i \not| m$ since it would need to be true that if $p_i|m$ and $p_i|4(p_1\cdots p_i \cdots p_n)$, then by the division theorem $p_i| [m - 4(p_1p_2\cdots p_n)] \implies p_i|3$. But, this isn't possible since we purposefully omitted $p_0=3$ from our definition of $m$, and hence $p_i > 3$. Therefore, (by another sub-contradiction) $p_i \not| m$. 
<br>
<br>
We also know that $m$ is odd because $\forall n\in\mathbb{N}$, $2|4n$ implies $4n$ is even. Then, adding 3 guarantees $4n+3$ will always be odd, and so will $m$. Therefore, the prime factors of $m$, which must come from the finite set $P$ are congruent to either 1 or 3 modulo 4. By construction, $m \equiv 3 (\text{mod }4)$. This means $m$ must have at least one prime factor $q \equiv 3 (\text{mod }4)$ (see the Multiplication Property of Modular Arithmetic). But, previously we showed that *none* of the finitely many primes in $P$ (which we have supposed to be all of those primes such that $p_i \equiv 3 (\text{mod }4)$) divide $m$. Therefore, there **must** exist a prime $p \equiv 3 (\text{mod }4)$ that is not in P! 

Therefore, we can conclude there are infinitely many primes $p$ such that $p \equiv 3 (\text{mod }4)$. 

Similarly to the previous prime generator, we have the algorithm:
1. $P = \{7\}$
2. $m = 4(7) + 3 = 31 \implies P=\{7,31\}$
3. $m = 4(7)(31) + 3 = 871 = 67(13) \implies P =\{7,13, 67\}$
4. $m = 4(7)(31)(67) + 3 = 58189 = 19(3061) \implies P =\{7,13,19, 67\}$

And so on and so forth {% cite silverman2012friendly %}:!

## Does the Euclid-Mullin Sequence contain all the primes?
**Short answer:** We don't know!

**Long answer:** But there is generalization that does contain all the primes!

Clearly, the Euclid-Mullin Sequence doesn't generate the primes in order. Where we left off in our example of the algorithm, we had
$$P = \{2,3,7,13,43,..\}$$

It's plain to see some of the primes are missing-- at least missing up through iteration $5$-- like $5, 11, 17, 19$. But, we already saw in our example the primes are not generated in order from least to greatest since we generated 43 before 13. This begs the question: does the Euclid-Mullin Sequence generate *all* the primes eventually?

This question was posed originally by the titular Mullin in 1963, but still this question remains open. Generally, we can create variations of the Euclid-Mullin sequence by varying that *seed* we begin the construction with. The *seed* is the initial set $P$ we begin the algorithm with, $P = \{p_1, \cdots, p_k\}$. In the case on the typical Euclid-Mullin sequence, $P = \emptyset$, with the convention that the empty product is 1. Depending on the seed we start with, it is demonstrable that some Euclid-Mullin sequence variations *do not* contain all the primes {% cite booker2016varianteuclidmullinsequencecontaining %}.

Basically, it is not known if there is a single seed that generates all the primes. But, interestingly the previously cited {% reference booker2016varianteuclidmullinsequencecontaining %} proves the *generalized* Eucild construction *does* in fact generate all the primes. The generalized Euclid construction is as follows: 

{% quote booker2016varianteuclidmullinsequencecontaining %} [I]f $\{p_1,\cdots, p_k\}$ is a set of prime numbers, then for any $I \subseteq \{1,\cdots,k\}$, the number 
$$N_I = \prod_{i\in I} p_i + \prod_{i\in\{1,\cdots,k\}\backslash I}p_i$$

is coprime to $p_1 \cdots p_k$ and has at least one prime factor. Iteratively
choosing a set $I$ and a prime $p_{k+1} | N_I$, we obtain an infinite sequence $p1, p2, \cdots$ of distinct prime numbers, as in Euclid’s proof. (Note that Euclid’s construction is the special case in which $I = \emptyset$ at each step.)
We call a sequence resulting from this more general construction a generalized Euclid sequence with seed $\{p_1,\cdots, p_k\}$. {% endquote %}

That's pretty complicated, and computationally dense-- but it is a cool result that a variation of the Euclid-Mullin Sequence is proven to generate all the primes.

## Some other functions known to generate all the primes
### Taking Advantage of Wilson's Theorem
There's actually other, better known functions that also generate all the primes. Some are based on Wilson's Theorem which states

> If $p\in\mathbb{N}$ is a prime number, then $(p-1)!\equiv -1 (\bmod p)$

{% cite Lauritzen2003 %}

Equivalently, if $p+1$ is prime $\iff$ (if and only if) $p! \equiv p(\bmod p+1)$. So, $\forall n \in\mathbb{N}$ 

$$f(n) = \Biggl\lfloor \frac{n!(\bmod n+1)}{n}\Biggr\rfloor(n-1)+2$$

It works because if $n+1$ is composite, then the term inside the floor function will be 0 (according to Wilson's Theorem), so the result for a composite $n+1$ will always be 2. If $n+1$ is prime, then the term inside the floor function will be a 1 (again, thanks to Wilson's Theorem!), then we are essentially just recovering $n+1$ by re-adding 2. {% cite Formulaforprimes %}
<br>
<br>
Of course, we know there are infinite natural numbers and they are countably infinite. We define the natural numbers cardinality as *aleph-null* that is $|\mathbb{N}| = \aleph_0$. This function serves as a bijection to the primes. Therefore, we can conclude that for the set of all primes, $\mathbb{P}$, the cardinality is the same as $\mathbb{N}$ and is also countably infinite. That is

$$|\mathbb{P}| = |\mathbb{N}| = \aleph_0$$

Another such method for generating primes utilizing Wilson's Theorem was given by Wilan's in 1964:

$$p_n = 1 + \sum^{2^n}_{i=1}\Biggl\lfloor \Biggl( \frac{n}{\sum^i_{j=1}\lfloor (\cos(\frac{(j-1)! + 1}{j})\pi)^2\rfloor}\Biggr)^{\frac{1}{n}}\Biggr\rfloor$$

Apparently, this reduces to

$$p_n = 1+\sum_{i=1}^{2^n}[\pi(i) < n>]$$

In other words, from {% reference Formulaforprimes %}:

{% quote Formulaforprimes %}
[T]hat is, it tautologically define $p_n$ as the smallest integer $m$ for which the prime-counting function $\pi(m)$ is at least $n$
{% endquote %}

### Mill's Formula
Another cool prime generating function was established by Mills in 1947. he proved there exists $A \in\mathbb{R}$ such that if

$$d_n = A^{3^n}$$

Then

$$\lfloor d_n \rfloor = \lfloor A^{3^n} \rfloor$$

is prime for all positive integers $n$ {% cite Formulaforprimes %}.

# Is This Useful?
**Short answer:** Some of it!

**Long answer:** Yes! Cryptography is field in which it is pretty useful. But, does number theory need to be useful to make it worth studying?

Probably the most applicable use for primes is in cryptography. Even though there's a plethora of functions that *can in theory* generate all the primes, all of these functions are **extremely** inefficient in terms of computational time and energy {% cite Formulaforprimes %}. In RSA encryption for example, we are picking two huge prime numbers (call them $p$ and $q$) and then acting on the massive resultant composite number from their product ($N = pq$). So, even if someone knew $N$, it would take a normal computer to find its prime factorization. So, essentially, coming up with random primes is easy, but finding specific ones is incredibly difficult.

Difficult at least for traditional computers-- Shor's Algorithm and quantum computing threaten the security of RSA encryption, because RSA can be broken if factoring large integers is computationally feasible {% cite Shorsalgorithm %}. But for now, you're safe! For more on RSA, see this [post](https://sara-pesso.github.io/epic-math-blog/blog/2026/RSA/). 

# Conclusion
In general, regardless of utility of number theory as a whole it is certainly worth studying. Any math that is proofs based and forces people think through and apply theorems to more deeply understand logic in its own right is a worthy endeavor-- especially in a world where mathematics as a field for humans is being threatened by AI. Just because AI may (or may not) be capable of greatly aiding human mathematicians in proving previously unproved conjectures (like the recent developments from OpenAI on the Millennia Problems) does not mean that we as a species should become complacent. If we abandon the study of mathematics simply "because a computer can do it better", we risk losing humanity's ability to think rationally and logically. 

Maybe a machine can do all this better, and solve every unsolved problem in Number Theory or mathematics in general, but let's not forget that *all* of these AI models are trained on the entire corpus of humanities accomplishments-- so they'd be useless without the likes of Euclid and Euler anyway.

Happy mathing!
- Sara 11/6/2026

