---
layout: post
title:  "CH2-Syntactic pitfalls"
date:   2019-04-28
categories: programming language
---

# Syntactic pitfalls

## understanding function declarations

```c
int i;

float ff();

float *pf;
//*pf is a float and therefore that pf is a pointer to a float

float *g();
/*
since () binds more tightly than *
g is a function that returns a pointer to a float
*/

float (*h)();
h is a pointer to a function returning float
```

example: the *signal* library function

```c
typedef void (*HANDLER)(int);
HANDLER signal(int, HANDLER);
```


## Operators don't always have the precedence you want

How to remember the precedence of the operators?

+ not really operators: () [] -> .

+ unary operators: ++ -- * & sizeof()

  from right to left

+ true binary operators

  + arithmetic operators

  + shift operators

  + relational operators

  + logical Operators

  + assignment operators: from right to left

  + conditional operators: from right to left

## Watch those semicolons

## The *switch* statement

## Calling functions

## The dangling *else* problem
