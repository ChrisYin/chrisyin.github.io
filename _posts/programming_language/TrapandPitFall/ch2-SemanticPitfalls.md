---
layout: post
title:  "CH3-Semantic pitfalls"
date:   2019-05-02
categories: programming language
---

# Semantic pitfalls

## Pointers and arrays

+ One dimensional arrays

```c
int calender[12][31]
//12 arrays of 21 int elements each
```

## Pointers are not arrays

+ remember free the memory allocated by *malloc* functions

+ call to *malloc()* may fail

## Array declarations as parameter

## Eschew synecdoche

## Null pointers are not null strings

The important thing to remember about 0 when used as a pointer is that *it must never be dereferenced.*

## Counting and asymmetric bounds

Use inclusive lower bounds and exclusive upper bounds.

## Order of evaluation

Only the four operators && || ?: , specify an order of evaluation.

, operator: evaluates its left operand and discards its value, then evaluates its right operand.

## The && || and ! Operators

## Integer Overflow

## Returning a value from main
