---
layout: post
title: 'AI & Fair Use'
date: 2026-09-22
description: Thoughts on Kevin Kelly's (Wired Magazine) article "Arguments in Favor of AI Fair Use"
tags: [AI, ethics]
categories: [blog]
featured: true
marimo: true
---

## NOTES:
1. AI does not "transform them into another kind of thing"-- LLMs, for example, tokenize all the words in a work, and does this for all the words in a corpus. This is *not* **at all** *in any way* changing the work. Tokenization is essentially just creating a map of how all the words in a work are arranged.

At it's simplest think of it like this: tokenization is taking the dictionary, mapping every word to a natural number. Then, the work is represented as the series of numbers that corresponds to each of the words. Words with the same root (like "jump" versus "jumping" versus "jumped") will get **stemmed** and have the suffixes removed, so the computer can recognize it as the same word(sometimes this process is called lemmatization). There are other ways data scientist clean up the data, but in reality they are not transforming it-- just representing it in a way a computer can understand. 

The same is done when representing pictures. The human-made works in the corpus, whether they started as a digital work or not, are represented by the computer using pixels of different colors, which again are assigned a numerical value. For grayscale, that is a number (0-255) where 0 is white and 255 is black. For RGB (red-green-blue) or color photos this is a vector with three (0, 255) values instead representing the intensity of red, green, and blue, respectively at each pixel. Again, this **represents** the picture as a matrix (or tensor) a computer can work with-- but it hasn't been changed. At this point, a data scientist might clean up these matrices using SVD or some other noise-suppressing methods, but the pictures haven't been changed.

Truly *transforming* the data at this stage-- in the way the spirit Fair Use is written-- wouldn't make any sense since the goal is for the computer to ingest the corpus of human knowledge, so it can spit it back out. 

The sentence "[t]he latent spaces of an LLM are closer to something like a syntax (sic)" is just a strange statement, but it's a good way to get into what AI (neural networks, whatever) are actually doing. I'll briefly speak on the math behind both because it's relevant. Kelly seems to focus mostly on LLMs. Basically, the latent space these create are an n-dimensional 
#####
#TODO

2. "Content can be moved into latent space, but the latent space cannot be reversed to go back into the original content. It has truly been transformed."
Hokum. 

3. "When an LLM is assigned the task of proving a math problem, it is not substituting for a book about math."

Wow, I think 

10. The spirit of copyright law... just because something is *legal* does not make it right. Case in point: abortion. 

I can see why this only has 83 likes. 

I actually really don't agree with a lot of these points. First of all, the way he talks about "latent space" makes it sound a lot more magical than it is. It's matrix algebra. In LLMs its tokenization of words and then an n-dimensional map of how those words relate to each other. Sometimes literally a representation of how far about these words exist from each other on the page. Neural networks are just an optimized linear combination of features from whatever data. An abstraction? Yes. Unique? No. LLMs/ AI though constantly being given more training data and changing the latent space (Kelly's favorite buzz word), are deterministic. And cannot exist at all without training it on a corpus of humanmade (copyrighted or otherwise works)

"The key benefit of LLMs is their smartness". Smartness? It's insanely good pattern recognition. These things CANNOT have an original thought. Everything they spew out existed before... Goedel proved this decades ago. I've actually wanted to write something about how AI "solves mathematical proofs".  By Goedel, these things are closed axiomatic systems (axioms that humanity figured out and then someone feed to an AI, btw) and will have blindspots. These blindpsots can only be filled by real intelligence, and then used by AI. See what actually happened with Erdos 90. 

He also misses the point that you are taking someone's work in order to build these things in the first place. 