---
layout: post
title: 'Dynamic Programming For Dummies - Pt. 3: SSQ as an Assignment Problem'
date: 2026-09-10
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

As aforementioned, in the LeetCode hat-assignment version of this problem, there can be more hats than people to assign them to-- but of course, for answering the SSQ, there are the same number of gift-givers as receivers. We will accommodate both of these possibilities. Again, we will use the terminology of assigning *objects* (rather than "hats" or "gift-receivers") to *nodes* (rather than "people" or "gift givers"). Our function will take an a Python list of lists (LOLs) as user-defined input:
```python
objs = [[0, 1, 2], 
        [2, 3], 
        [0, 1], 
        [3, 4]]
```
In this example, node $1$ can be assigned objects $[2,3]$. Generally, in this list of list, $C_ij$ represents the fact that node $i$ can be assigned object $j$. Each row $C_i$ (which can be over varying length), represents the set of all objects node $i$ may be assigned. 

1. First, we need to turn our input LOLs (which maps node $i$ to allowed objects) into a list of dictionaries that maps each *object* to those nodes which it is allowed to be assigned. Dictionaries are a better choice versus a list here, because we do not need to know the total number of objects beforehand, like we would need to initialize a LOLs. For example, our earlier example would become:
```python
obj_to_node = defaultdict(list)
    for i, allowed_objs in enumerate(objs):
        for obj in allowed_objs:
            obj_to_node[obj].append(i)
    obj_to_node = list(obj_to_node.items())
```
```python
[(0, [0, 2]), (1, [0, 2]), (2, [0, 1]), (3, [1, 3]), (4, [3])]
```
Object 3 can be assigned to node 1 or 3, and so on.

2. Initialize final bitmask and DP (memoization) table. 
Now, we have the reverse mapping, make it easy to determine what pairings are allowed, regardless of whether we know the node or object. We can easily find the number of nodes, and then create our stop criteria: we will break out of our loop when we hit assign all nodes an object (a successful assignment permutation)-- which is equivalent to a bitmask of all ones: 
```python
n = len(objs)
fin = (1 << n) - 1
```
We'll initialize our dp as
```python
dp = {}
```
The DP table will end up being a map of tuple (object $i$ assigned, bitmask) to the running count of the number of permutations possible **after** that combination.

3. After that, we can start DFS. Applied to our assignment algorithm, DFS works as follows: Starting with any object (call it object $i$), we attempt to assign assign object $i$ to each node $j$-- checking if the assignment is allowed and checking our bitmask for whether or not node $j$ has already been assigned. If it's possible, we then assign object $i$ to node $j$ in the bitmask, and DFS recurses. Once the bitmask is "full" (that is, the bitmask is all ones indicating that every node has been successfully assigned an object), we add one to our successful permutations count.

In Python, we do this by creating a DFS function, that recursively takes the object index $i$, and current bitmask
```python
def dfs(i, mask):
```
Then, we'll do our checks. To reiterate:
1. Is the bitmask all ones, indicating we've successfully assigned an object to each node? If so, return 1 to add to our count of permutations
2. If the bitmask is not full, but the current object index is $n+1$, return 0. This means we have iterated through all $n$ objects, but at least one node is still not assigned. So, we do not have a successful permutation, and we add nothing to the count.
```python
if mask == fin:
            return 1

if i == len(obj_to_node):
            return 0 
```
3. Check the memoization (DP) table to see if we've completed this subproblem before. Recall the DP table is storing the current object index being assigned at the current bitmask to the running count of possible permutations after that combination. So, checking for the already solved subproblem and returning that result instead of recursing:
```python
if (i, mask) in dp:
            return dp[(i, mask)]
```

4. DFS Skip! We do this so we can see if we can assign an object to every node without this particular object. This way we can get accurate counts for all $P(n,k)$ permutations (this notation means "choose $k$ objects from $n$ total objects, where the order matters). Note: this step really only matters if there are less nodes than objects! In the case of the SSQ, this step is moot, but doesn't do any harm. This is also how we can start tracking the *total* number of permutations possible!
```python
num_perms = dfs(i + 1, mask) 
```
5. DFS: Loop through each object and then in a nested loop, loop through all the nodes to which that object is able to be assigned. 
    - a. If the current node is already assigned (i.e., the corresponding bit in our mit mask is already set to 1), skip to the next node. 
    ```python
    for node in obj_to_node[i][1]:
        if mask & (1 << node):
            continue
    ```
    - b. If the current node hasn't yet been assigned an object (i.e., the corresponding bit is a 0 in the current bitmask), assign the current object and then update the bitmask by setting the node's bit to 1. 
    ```python
    new_mask =  mask|(1 << node)
    ```
    - c.  Recurse by running the DFS step again, moving on to the next object's index and the new bitmask (keeping track of which nodes have already been assigned in our callstack)
    ```python
    num_perms += dfs(i + 1, new_mask)
    ```

6. Once we're done looping through all the objects and assigning them as we can, the loop will end. Before we exit this branch of the DFS, we can then update our DP table for the number of permutations found starting from object $i$ and the original mask.
```python
dp[(i, mask)] = num_perms
return num_perms
```
7. Finally, once DFS is complete the function terminates, returning the total number of possible permutation, the memoization table, and our object-to-node list of dictionaries.
```python
return dfs(0,0), dp, obj_to_node 
```
As each DFS object and current bitmask are iterated through, this saves the total permutations possible **after** that object is assigned within the possibilities decoded from the current bitmask. This means that in our DP table, tuple $(i = 0, bitmask = 0)$ maps to the total count of permutations. We can also use this fact to easily decode a unique assignment from the resultant DP table. 

So, after we define our LOL and call the function, we'll save the number of permutations, memoization table, and the object-to-node map as some variables:
```python
objs = [[0, 1, 2], 
        [2, 3], 
        [0, 1], 
        [3, 4]]

count, dp, mappings = assignment_permutations(objs)
```
### Extracting a Unique Solution from the Memoization (DP) Table
I think this is the most fun part of this algorithm. We are going to use the memoization table to work forwards through all the bitmasks and information we saved to find one assignment solution. Something I'd like to eventually do with this part of the algorithm is make it randomly traverse bitmasks, so the user gets a different, valid assignment each time. So much to do!

1. First, make sure there is at least one solution.
```python
if dp[(0,0)] == 0: 
    print("There is no unique assignment of objects to the nodes in this matrix.")
```
2. If there is at least one unique assignment solution, we'll need to grab the number of objects. We will also initialize our bitmask to $0$ (i.e., nothing is assigned). And, again define the "full mask"-- a bitmask of all ones we'll use as our stopping criteria. 
```python
num_objs = max(map(max, objs)) 
current_mask = 0
full_mask = (1 << num_objs) - 1
```
3. Initialize a dictionary to hold the assignment pairings
```python
assignments = {}
```

4. Begin looping thru the index of each object. Then, check if all the
```python 
for i in range(num_objs):
```

5. Set a flag that will indicate whether this object is assigned. If it happens that this object is assigned to some node in the assignment permutation being mapped from the DP table, this flag will be set to ```True```. When the loop moves on to object $i+1$, this flag will be reset to ```False```. 
```python
assigned_obj = False
```
6. Attempt to assign object $i$ to some node $j$ by looping through each allowed node in the *object-to-node* mapping derived from the user defined input matrix. By comparing these to the number of possible permutations counted up **after** each bitmask (which we have mapped in the memoization/DP table), we can determine if node $j$ is actually a viable pairing for object $i$. For example, if we see that in the object-to-node map object $i$ is allowed to be assigned to node $j$ and this assignment can lead to viable permutations via the DP table, we can report it in our final assignment. But, if the DP table indicates there are 0 ways to make a viable full assignment after assigning object $i$ to node $j$, we can not do it. 
```python
for j in mappings[i][1]:
```
Here's the fleshed out steps to this:
- a. Verify node $j$ is not already assigned in the current mask (i.e., make sure the $j^{th}$ bit is $0$).
```python
    if not (current_mask & (1 << j)):
```

- b. Compare assigning object $i$ to node $j$ in the current bitmask, to viable assignments for object $i+1$ in the next bitmask (assuming that we continue with this particular assignment). If the next mask is the full mask, then we don't need (or have to) assign any more objects to nodes. Then, verify that the number of possible permutations counted after object $i+1$ and the new bitmask stored in the DP table is greater than 0 (i.e., there is at least one path to a complete assignment). 
```python
    new_mask = current_mask | (1 << j)
    if new_mask != full_mask:
        if dp[(i + 1, new_mask)]:
```

- c. Assuming all these checks are passed, assign object $i$ to node $j$ in the dictionary, move on to evaluating the new bitmask, and switch the flag to ```False```. Finally, break out of the loop and move on to object $i+1$.
```python
            assignments[j] = i
            current_mask = new_mask
            assigned_obj == True
            break
```

- d. If the new mask is the bitmask of all ones (the full mask), make the final assignment and break out if the loop.
```python
    else: 
        assignments[j] = i
        break   
```

- e. For the sake of saving a bit of speed, if we've reached the full mask and previous object was able to be assigned, we are done and can break out of the nested loops. 
```python
if assigned_obj and current_mask == full_mask:
    break
```

### Conclusion
Then, we can print out the results! Now, you can apply this to both LeetCode 1434 and the SSQ. We simply need to make an input matrix that appropriately describes allowed pairings between the participants. In my [current GUI](), it in takes a CSV file-- that the user can select-- which describes the *exclusions* between the participants. So, we'd need to add a preprocessing function to our code base that transforms that exclusion table into a matrix of the correct form. 

I find it a really fun exercise to approach the same problem from multiple angles, like I'm doing with this dynamic programming series. I, personally, could think of three different DP heuristics which could solve the Secret Santa Question my MIL asked me about-- and there's plenty of other ways to solve this (some of which are even better, then anything I could come up with!) that people way smarter than me could come up with. 

Happy programming!

- Sara 9/10/2026

## Python Code
This script can be found on [my Github!]()
Here is a working version of algorithm we walked through above.

<div class="al-marimo-inline" markdown="1">

```python
from collections import defaultdict

def assignment_permutations(objs):
    # 0. First, we need to turn our input LOLs (which maps node $i$ to allowed objects)
    # into a list of dictionaries that maps each *object* to those nodes which it 
    # is allowed to be assigned.
    obj_to_node = defaultdict(list)
    for i, allowed_objs in enumerate(objs):
        for obj in allowed_objs:
            obj_to_node[obj].append(i)
    obj_to_node = list(obj_to_node.items())

    # 1. Initialize memoization (DP) table and final bitmask
    # Find the number of nodes to which we will assign objects.
    n = len(objs)

    # Also need to define our stop criteria. All ones in our bitmask 
    # means that every node has been assigned (an allowed) object. So, we know we
    # can break out of our loop.
    fin = (1 << n) - 1 

    # Initial DP Table
    dp = {}


    def dfs(i, mask):
        # 1. Check if every node has successfully been assigned an object.
        # If so, return 1 (adding 1 to our successful permutations count)
        if mask == fin:
            return 1

        # 2. If the bitmask is not full, but the current object index is n+1, return 0. 
        # This means we have iterated through all n objects, but at least one node is still not assigned. 
        # So, we do not have a successful permutation, and we add nothing to the count.
        if i == len(obj_to_node):
            return 0 

        # 3. Check the memoization (DP) table to see if we've completed this subproblem before. 
        # Recall the DP table is storing the current object index being assigned at the 
        # current bitmask to the running count of possible permutations after that 
        # combination. So, checking for the already solved subproblem and returning that 
        # result instead of recursing:
        if (i, mask) in dp:
            return dp[(i, mask)]

        # 4. DFS Skip! We do this so we can see if we can assign an object to every node without
        # this particular object. This way we can get accurate counts for all P(n,k) permutations.
        # (this notation means "choose $k$ objects from $n$ total objects, where the order matters).
        # Note: this step really only matters if there are less nodes than objects! In the case
        # of the SSQ, this step is moot, but doesn't do any harm.
        # This is also how we can start tracking the *total* number of permutations possible!
        num_perms = dfs(i + 1, mask) 

        # 5. DFS: Loop through each object and then in a nested loop, loop through all the nodes
        # to which that object is able to be assigned. 
        for node in obj_to_node[i][1]:
            # a. If the current node is already assigned (i.e., the corresponding 
            # bit in our mit mask is already set to 1), skip to the next node. 
            if mask & (1 << node):
                continue

            # b. If the current node hasn't yet been assigned an object (i.e., the corresponding bit 
            # is a 0 in the current bitmask), assign the current object and then update the bitmask by 
            # setting the node's bit to 1.
            new_mask =  mask|(1 << node)

            # c. Recurse by running the DFS step again, moving on to the next object's 
            # index and the new bitmask (keeping track of which nodes have already been 
            # assigned in our callstack)
            num_perms += dfs(i + 1, new_mask)

        dp[(i, mask)] = num_perms
        return num_perms
    
    # 7. Finally, once DFS is complete the function terminates, returning the total 
    # number of possible permutation, the memoization table, and our object-to-node 
    # list of dictionaries.
    return dfs(0,0), dp, obj_to_node 

### ==== MAIN FUNCTION ====
objs = [[0, 1, 2], 
        [2, 3], 
        [0, 1], 
        [3, 4]]

count, dp, mappings = assignment_permutations(objs)

### ==== EXTRACT UNIQUE ASSIGNMENT ====

# 1. First, make sure there is at least one solution.
if dp[(0,0)] == 0: 
    print("There is no unique assignment of objects to the nodes in this matrix.")

else: 
    # 2. If there is at least one unique assignment solution, we'll need to grab the 
    # number of objects. We will also initialize our bitmask to 0 
    # (i.e., nothing is assigned).
    # And, again define the "full mask"-- a bitmask of all ones we'll use as our stopping criteria. 
    num_objs = max(map(max, objs)) 
    current_mask = 0
    full_mask = (1 << num_objs) - 1

    # 3. Initialize a dictionary to hold the assignment pairings
    assignments = {}

    # 4. Begin looping thru the index of each object
    for i in range(num_objs):

        # 5. Set a flag that will indicate whether this object is assigned. If it 
        # happens that this object is assigned to some node in the assignment 
        # permutation being mapped from the DP table, this flag will be set to True.
        # When the loop moves on to object i+1, this flag will be reset to False. 
        assigned_obj = False

        # 6. Attempt to assign object i to some node j by looping through each allowed node 
        # in the object-to-node mapping derived from the user defined input matrix. By comparing 
        # these to the number of possible permutations counted up after each bitmask (which we 
        # have mapped in the memoization/DP table), we can determine if node j is actually a 
        # viable pairing for object $i$. For example, if we see that in the object-to-node map 
        # object i is allowed to be assigned to node $j$ and this assignment can lead to viable 
        # permutations via the DP table, we can report it in our final assignment. But, if the 
        # DP table indicates there are 0 ways to make a viable full assignment after assigning 
        # object i to node j, we can not do it.
        for j in mappings[i][1]: 

            # a. Verify node j is not already assigned in the current mask (i.e., make sure the 
            # jth bit is 0)
            if not (current_mask & (1 << j)):

                # b. Compare assigning object i to node j in the current bitmask, to viable 
                # assignments for object i+1 in the next bitmask (assuming that we continue 
                # with this particular assignment). If the next mask is the full mask, then we 
                # don't need (or have to) assign any more objects to nodes. Then, verify that 
                # the number of possible permutations counted after object i+1 and the new 
                # bitmask stored in the DP table is greater than 0 (i.e., there is at least one 
                # path to a complete assignment).
                new_mask = current_mask | (1 << j)
                if new_mask != full_mask:
                    if dp[(i + 1, new_mask)]:

                        # c. Assuming all these checks are passed, assign object i to node j in 
                        # the dictionary, move on to evaluating the new bitmask, and switch the 
                        # flag to False. Finally, break out of the loop and move on to object i+1.
                        assignments[j] = i
                        current_mask = new_mask
                        assigned_obj == True
                        break

                # d. If the new mask is the bitmask of all ones (the full mask), make the final 
                # assignment and break out if the loop.
                else: 
                    assignments[j] = i
                    break

        # e. For the sake of saving a bit of speed, if we've reached the full mask and previous object was 
        # able to be assigned, we are done and can break out of the nested loops. 
        if assigned_obj and current_mask == full_mask:
            break

## ==== FINAL SOLUTION! ====
for i in assignments:
    print(f"Node {i} --> Object {assignments[i]}")
```

</div>