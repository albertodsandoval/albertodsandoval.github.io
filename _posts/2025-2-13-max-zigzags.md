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

This blog post will explre the logic behind my solution
for the Max Zig-Zag problem in an array of integers I will
also dive into the thought processes and challenges I faced
when trying to identify an algorithm to solve it. The
problem was assigned to us by Professor John Noga's 
COMP 482 (Algorithm Design and Analysis) course offered at CSUN.

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
the steps I might take ion real life to get the desired outcome. 
![Image](/assets/images/Max-Zig-Zags.png)

My first thought was to sort the books based on their height (Tallest to shortest)
and then split the stack of books in half. Then do some sort of zip operation where
we alternate books from the first half and the second half. My idea was, since we
sorted the books by height, we know that the books in the second half will all be
shorter than or equal to the books in the first half. This is crucial to the
functionality of this algorithm since (assuming the set has all different numbers)
we know that any number in the second half will be smaller than any number in the
first half. So alternating between the second half (smaller half) and the first half
will guarantee zig-zags. As an example, we can take the input:
```java
5
1 2 3 4 5
```
Then we can sort it and split it.
```java
5 4 3   2 1
```
Here is where I realized there will be an issue with odd numbers, so for now I just give
the half larger in value the extra number. Which then zips into:
```java
5 2 4 1 3
```

This gave us a pattern with 4 zig-zags, but at this point I wasn't sure if this was correct
solution. The solution definitely **cannot** be lower than 4, because we know a case with 4 
**exists**. But can it be above 4?

The answer is actually NO! If you have 5 numbers, it is impossible to have more than 4 zig-zags. 
This is because one zig-zag requires the _connection_ of 2 numbers, and in a set of 5
numbers we only have 4 _connections_. This is an important discovery for me because I
now know that the max amount of zig-zags in a given set of numbers of size n is n-1.

## Testing! Testing! Testing!

After testing a few more simple cases and seeing success in the algorithm, I started to
search for edge cases and starting categorizing the type of tests I was feeding the algorithm.
By the logic of the naive algorithm, the **ideal** case is where all the numbers are different.
But what if all the numbers were the same? Well if all books were the same height, there's no 
zig-zags! Simple. Now, what if a large majority of the numbers are the same? Lets test it. Take:
```java
10
1 1 1 1 1 1 1 2 3 4
```
Here there are 7 one's and 3 unique integers. Lets preform our algorithm.
```java
4 3 2 1 1   1 1 1 1 1
```
```java
4 1 3 1 2 1 1 1 1 1
```
You can see here that we only have 5 zig-zags, on an input of size 10 the maximum possible is 9.
So either the algorithm is malfunctioning or this case truly only has 5 zig-zags. Notice the 1's,
is there any way that we can organize the 1's such that they do NOT touch each other? If two numbers
that are the same are touching, that wouldn't be an increase OR a decrease, lets call it a straight.
Straights instantly subtract 1 from our zig-zags, and in our case we have 4. This is why we only have
5 zig-zags since we subtract the straights from the max zig-zags. Here the question was, _is there 
a way to organize these 1's so that they do not touch?_. Lets try:
 ```java
1 2 1 3 1 4 1 1 1 1
```
Here we reduced the consecutive 1's from 5 to 4, which gave us one more zig-zag. The algorithm failed, but
could be fixed with some tweaks. Lets first figure out how many times a number can repeat before the number
**must** come into contact with itself, causing a straight. Let's use X's and O's to try to figure this out.
In the case of an odd number input size:
```java
X O X O X O X O X
```
The way to maximize the spread of X's without letting them touch is by alternating them, and in an odd number 
we can have one more X than O's. This is n/2+1, where n is the input size.
Instead of alternating starting from the larger half constantly, we can
try alternating from the larger half first **and also** from the smaller half first. This is because one of
these halfs must contain the number that repeats a **lot**, and we want to START with that number to 