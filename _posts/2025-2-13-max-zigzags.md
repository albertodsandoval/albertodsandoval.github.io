---
title: "Maximum Zig Zags In Number Array (Java)"
date: 2025-2-13
categories:
  - Blog
tags: 
  - Lesson
  - Algorithm
  - Proofs
---

This blog post will explain my logic behind my solution
for the Max Zig-Zag problem in an array of integers. The
problem was assigned to us by Professor John Noga in the 
COMP 482 Algorithms course offered at CSUN.

## The Problem (Max Zig-Zags)

The **computational problem** at hand is to determine the maximum
amount of _zig-zags_ in a set of integers. A zig-zag is described 
as a increase followed by a decrease or vice versa. These increases
and decreases are based on the value of the integers, so for example 1 2 
would be an increase while 2 1 would be a decrease. As an example:
```java
1 2 1 2 1
```
would have 4 zig-zags since the value of the integer alternates from increasing
to decreasing 4 times. 

One thing to watch out for are _double decreases_ or _double 
increases_. These are described by either 2 consecutive increases or 2
consecutive decreases in integer value. An example of a double increase
would look something like this:
```java
1 2 3 1
```
we can see there is only 2 zig-zags in this example. But, that is not to
say that 2 is the maximum number of zig-zags in this set of integers. We
_could_ organize the numbers in this sort of fashion:
```java
1 2 1 3
```
and here it is clear that there are 3 zig-zags compared to the previous 
example with only 2.

The **input** for the problem states the size of the integer array
followed by the values of the array. An example of a **problem instance** 
may look like:
```java
5
1 2 3 4 5
```

You may be quick to think the **solution** to this problem may look
something like:
```java
5 2 4 1 3
```
since this maximizes the amount of zig-zags. But the goal is not to
find a specific pattern containing the maximum amount of zig-zags, but
instead you just simply need to find the maximum amount of zig-zags. So
the actual solution is simply:
```java
4
```

## Initial (Naïve) Approach

The quickest method I was able to come up with to solve this problem
is probably the most obvious and the majority of people first thought:
brute force.

The idea is to determine all possible ways to organize the numbers.
As you are determining all these cases, you also count the amount of zig-zags
and keep track of the largest number. After iterating through all the possibilities
you will then know then know what the maximum amount of zig-zags is because you
officially tested all existing possibilities!

Sounds great and simple, but if you have any background or experience in
statistics you know this is a nPn permuation. Where in an input
of size n, we have n options to choose the first number, n-1 options for the 
second, n-2 options for the third, and so on. This ultimately boils down
to n! (factorial for those unfamiliar) different ways to organize n numbers
(when order matters, which it does).

Not only would we have to create n! different test cases, but we would also
have to count the amount of zig-zags in each case. Counting zig-zags requires
we loop through the entire array of size n at least one time, so for each of 
the n! cases we would have at n operations! As an example, if we had an input
of size 5, we would have 5! different cases. Thats 120 different ways we can 
organize the 5 numbers! And for each of those 120, we would have at least 5 
_additional_ operations, boosting the total amount of operation to at least
600, and that is being generous. Increasing the input size even just a little,
would increase the total operations number **drastically**. For an input of size
7, the operations would add up to at least 35280.

Professor Noga specified that the cases he would be testing us on would go up
to size 100. The amount of operations for a size 100 input would be at least
9.3 x 10<sup>156</sup>. A truly ridiculous number. This would not do, so I asked myself:

## How Would One Approach This Problem In Real Life?

So far in the lecture for this course (Algorithm Design and Analysis) we have
gone over one computational problem, Stable Matching. The way Professor Noga
made the solution intuitive to understand was by asking us how we would deal
with the situation in real life. From there we were able to conclude the 
[Propose - Dispose](https://en.wikipedia.org/wiki/Gale%E2%80%93Shapley_algorithm)
algorithm. For those unfamiliar, it is interesting and worth reading about if 
you are interested in these sort of things.

So I looked at a visual example provided by Professor Noga and thought about
the steps I might take to get to the solution. 
![Image](/assests/images/Max-Zig-Zags.png)


