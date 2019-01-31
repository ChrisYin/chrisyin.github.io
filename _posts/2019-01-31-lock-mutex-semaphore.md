---
layout: post
title:  "Chapter5: Synchonizing Access to Shared Objects"
date:   2019-01-31
categories: operating system
---
# Chapter Five: Synchonizing Access to Shared Objects
When cooperaing thread share state, writing correct multi-threaded programs becomes much difficult.

## Challenge

+ Race Conditions: interleaving of operations of different thread.

+ Atomic Operations: indivisible operations

+ Too Much Milk: Even we can carefully reason about the possible interleavings, doing so is tricky and error-prone.[Safty and Liveness]

Three Solutions are put up.


+ Discussion: 

Memroy Barriers: no accesses before the barrier are moved after the barrier and no accesses after the barrier are moved before the barrier.

+ A better Solution
introducing lock and conditional variables.


## Structuring Shared Objects

+ Implementing Shared Objects

  - Shared Objects: bounded buffer, barrier
  - Synchronization Variables: Semaphores Locks Condition Variables
  - Atomic instructions: interrupt diable, test-and-set
  - hardware: multiple procesors, hardware interrupts
  

## Locks: Mutual Exclusion

A lock is a synchronization variable that provides **mutual exclusion**.

+ locks: API and Properties
  + lock:acquire and lock::release
    two states: busy and free  
    initially in the free state  
  
  + three properties:

    - Mutual exclusion
	- progress
	- bouded waiting
 

## Condition Variable: Waiting for a Change

Condition variable provide a way for one thread to wait for another thread to take some action.

+ Condition variable Definition

A condition variable is a sunchronization object that lets a thread efficiently wait for a change to shared state that is protected by a lock.
  
  + CV::wait  release the lock and suspend execution of the calling thread
  + CV::signal takes one thread off the conditon variable's waiting list
  + CV::broadcast: takes all thread off the condition variable's waiting list

## Designing and Implementing Shared Objects

## Three Case Studies

### Readers/Writers Lock

### Synchronization Barriers

check whether all threads are checked in.

### FIFO Blocking Bounded Queue

## Implementing Synchronization Primitives

## Semaphores Considered Harmful

Semaphore: still widely used

To use a semaphore as a mutual exclusion lock, initialize it to 1. Then, Semaphore::P is equivalent to Lock::acquire, and Semaphore::V is equivalent to Lock::release.

### different locks

Spinlock: loop to wait for release  used to small critical section

ticket lock: there is a queue.

Mcslock: linked list

clh lock: linked list


