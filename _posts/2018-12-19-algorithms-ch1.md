---
layout: post
title:  "Algorithms-Chapter One: Fundamentals"
date:   2018-12-19
categories: algorithms
---
# Fundamentals
## Bags, queues, and stacks

---
+ LIFO: last in first out
+ FIFO: first in first out

---
three data *types/structures*:
+ bags
+ FIFO queue
+ LIFO stack
  evaluation example

---
three features:
+ generics
+ autoboxing
+ iterable collection

---
algorithm1.1  
Pushdown stack: using interface  

---
Linked lists: a new data structure  
data structures:
+ array: sequential
+ linked list: linked allocation

## Analysis of algorithms
Mathematical model
+ Tilde approximations
+ Approximate running time
  + doubling test
  + doubling ratio test
+ cost model

---
Order-of-growth classifications
+ constant
+ logarithmic
+ linear
+ linearithmic
+ quadratic
+ cubic
+ exponential

---
Designing faster algorithm
+ 2-sum
  + brute-force: N^2
  + fast: N\*logN  
	mergesort + binary search  
	mergesort: N\*logN  
	binary search: logN  
+ 3-sum
  + brute-force: N^3
  + fast: N^2*logN  
	merge sort: N * logN  
	binary search: N(N-1)/2 * logN  

---
Coping with dependence on inputs
+ input models
+ worst-case performance guarantees
+ randomized-algorithms
  + quick sort: linear to quadratic
+ amortized analysis

---
Memory
+ primitive
+ objects
+ references
+ linked lists
+ arrays
+ strings

## Case Study: Union-Find

---
Dynamic connectivity
+ symmetric
+ transitive
+ reflexive

---
Union-Find API

>public class UF  
>void union()  
>int find()  
>boolean connected()  
>int count()  

---
Implementations & analysis

Cost model: array accesses of union function

+ Quick-find  
  2 + N + [1, N-1] = [N+3, 2N+1]
+ Quick union  
  2* (2 * depth + 1) + 1
+ Weighted quick union  
  depth <= logN
