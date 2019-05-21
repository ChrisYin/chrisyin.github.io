---
layout: post
title:  "CH7-Portability Pitfalls"
date:   2019-05-05
categories: programming language
---

# Portability pitfalls

## Coping with change

ANSI C -> C99

## What's in a name?

External variables: beginning six characters -> 31 characters

## How big is an integer?

Using typedef macro

## Are characters signed or unsigned?

(unsigned)(char c): fails because when converting a char quantity to unsigned, it is converted to int first.

(unsigned char)(char c): converting char to integer automatically

## Shift operators

A right shift of a signed integer is not equivalent to division by a power of two.

## Memory location zero

## How does division truncate?

Three properties:

+ q*b + r == a

+ change the sign of a -> change the sign of b

+ b>0 -> r>=0 && r<b

## How big is a random number?

define RAND_MAX

## Case conversion

Assume the input character is in appropriate case.

## Free first, then reallocate?

The seventh edition of the reference manual for the UNIX system described: you can free and reallocate later.

## An example of portability problems

+ get number from characters: +'0'

+ n = -n may overflow

+ % get remainder: the sine is not correct

 
