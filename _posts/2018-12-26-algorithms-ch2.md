---
layout: post
title:  "Algorithms-Chapter Two: Sorting"
date:   2018-12-26
categories: algorithms
---
# Elementary Sorts
---
Rules of the game

+ API  
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
