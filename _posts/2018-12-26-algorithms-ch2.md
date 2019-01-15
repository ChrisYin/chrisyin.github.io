---
layout: post
title:  "Algorithms-Chapter Two: Sorting"
date:   2018-12-26
categories: algorithms
---
# Elementary Sorts
---
Rules of the game

+ API of sorting algorithms  
  + less()
  + exch()

+ sorting cost model  
  count compares and exchanges

+ extra memory  
  divided into two different types according to memory usage

+ types of data  
  total order 

---
selection sort  
find the smallest item and exchange it with the first entry.
+ proposition: ~n^2/2 compares and n exchanges

---
insertion sort  
insert each into proper place among sorted place.
+ proposition: (average)~n^2/4 compares and ~n^2/4 exchanges
+ *partially sorted array*: inversions less than multiple of the array size

---
shell sort  
produce partially sorted arrays.  
rearrange the array to give it the property that taking every hth entry.

# Mergesort

---
abstract in-place merge

+ in-place : using aux array  
	
---
top-down mergesort/bottom-up mergesort

Complexivity: MergeSort uses at most NlgN compares and 6NlgN array accesses  
Proof: using upper bound lower bound formula

Memory: Mergesort uses extra memory proportional to N.

---
improvements:

+ use insertion sort for small subarrays.
+ stop if already sorted.


---
the complexity of sorting

+ compare-based sorting algorithms:  ~NlgN(lgN!)  
+ Nergesort is an asymptotically optimal compare-based sorting algorithm  

# Quicksort

---
basic alorithms

+ chose pivot  
+ partitioning: two pointer exchange  

---
implementation details:

+ partitioning inplace
+ staying in bounds
+ perserving randomness
+ terminating the loop
+ handling items with keys equal to the partitioning item's key
+ terminating the recursion

---
complexity:

+ ~NlgN compares
+ worst case: N^2/2

---
entropy-optimal sorting

+ quick-sort with 3-way partitioning  
  lower equal and larger

# Priority Queues

---
API:
```c++
class maxPQ
	+ insert
	+ max()
	+ delMax()
	+ isEmpty()
	+ size()

```

---
Elementary implementations

+ unordered array
+ ordered array
+ linked-list
+ orderred-heap

---
heap-based priority queue

+ definition: binary heap
+ algorithms on heaps: swim and sink
+ heap-based priority queue: insert and remove the maximum
+ complexity: 1+lgN compares for insert and 2lgN compares for remove the maximum

---
heapsort

+ heap constrction: nlgn
+ sortdown
+ complexity: 2nlgN compares and exchanges

# sorting applications

---
Sorting various types of data

---
which sorting algorithms should I use?

+ selection sort 
  unstable inplace N^2 1
+ insertion sort
  stable inplace [N, N^2] 1
+ shellsort
  unstable inplace N^6/5 1
+ quick sort[star]
  unstable inplace NlgN lgN
+ 3-way quicksort
  unstable inplace [N, NlgN] lgN
+ mergesort[star]
  stable newplace NlgN N
+ heapsort
  unstable inplace NlgN 1


---
reduction
+ duplicates
+ rankings
+ priority queue reduction
+ median and order statistics: liner time
