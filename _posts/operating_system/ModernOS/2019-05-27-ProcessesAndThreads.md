---
layout: post
title:  "Chapter2: Processes and Threads"
date:   2019-05-27
categories: Modern Operating System
---

# Processes

## The Process Model

+ Multirogramming: switch back and forth

## Process Creation

+ System initialization
+ Execution of a process creation system call by a running process
+ A user request to create a new process
+ Initiation of a batch job

## Process Termination

+ Normal exit
+ Error exit
+ Fatal error
+ Killed by another process

## Process Hierarchies

Parent process and child process

## Process States

+ Running 
+ Ready
+ Blocked

Four Transitons are between these three states

## Implementation of Processes

Process Table or Process Control Blocks

+ Process Management
  + Registers
  + Program Counter
  + ...
+ Memory Management
  + Pointer to text segment
  + Pointer to data segment
  + Pointer to stack segment
+ File Management
  + Root directory
  + User ID
  + ...

Implementation of Interrupt

# Threads

## The Thread Model

Two Concepts of Process:
+ Resource grouping
+ execution  -> thread

What threads add to the process model is to allow multiple executions to take place in the same process environment, to a large degree independent of one another.

Process Items:
+ Address space
+ Global variables
+ Open files

Threads Items:
+ Program Counter
+ Registers
+ Stack
+ State

## Thread Usage

Advantages:
+ multiple activities
+ easier to create and destroy
+ performance argument
+ share the addresss space and file descriptor

Examples of Multi-thread

Three Models
+ Threads: Parallelism and blocking system calls
  + multi-threaded Web server
+ Single-threaded process: No Parallelism, blocking system calls
  + single-threaded Web server
+ Finite-state machine: Parallelism, non-blokcing system calls, interrupts, but not sequential

## Implementing Threads in User Space

Advantages:
+ thread scheduling is fast: No Context Switch
+ Each process has its own scheduling algorithm

Disadvantages:
+ Blocking system call
+ How to schedule thread? Need intrrupts

## Implementing Threads in the Kernel

Advantages:
+ Not require nonblocking system calls

Disadvantages:
+ great cost of creating and destroy threads

## Hybrid Implementation

kernel threads

## Scheduler Activations

Using the mechanism called **upcall**

## Pop-Up Threads

Create Pop-Up thread quickly

## Making Single-Threaded Code Multithreaded

Problems:
+ private global variables
+ reentrant library procedure
+ signals to which thread?
+ stack management: grow which thread's stack?

# Interprocess Communication

Three problems:

+ communication
+ critical region
+ running order

## Race Conditions

where two or more processes are reading or writing some shared data and the final result depends on who runs precisely, are called race conditions.

## Critical Regions

Four Conditions
+ No two processrs may be simultaneously inside their critical regions
+ No assumptions may be made about speeds or the number of CPUs
+ No process running outside its critical region may block other processes
+ No process should have to wait forever to enter its critical region

## Mutual Exclusion with Busy Waiting

### Disabling Interrupts

unattractive: unwise to give user process the power to turn off the interrupt

### Lock Variables

Has the same problem: race condition of lock variable access

### Strict Alternation

Violates Conditon 3 and requires that the two processes strictly alternate in entering their critical regions.

### Peterson's Solution

Using Local Variables For Each Process

### The TSL Instruction

**Need Hardware Support**

TSL: Test and Set Lock

```
TSL RX, LOCK
//reads the content of the memory word lock into register rx and then stores a nonzero value at the memory address lock.
//atomic operation
```

## Sleep and Wakeup
Two Problems of the prior methods:
+ Busy waiting problems
+ Priority Inversion Problems

### The Producer-Consumer Problem

## Semaphores

Operation P: put down
+ greater than 0: decrement
+ is 0: sleep

Operation V: put up
+ finish P operation: value becomes zero
+ increment value

Semaphores in the producer-consumer problem
+ three semaphores
  + mutex exclusion: binary semaphore
  + empty and full semephores

## Mutexes

A simplified semaphore: mutex

The difference between mutex and lock variables: the latter one is busy waiting, but the former one use thread_yield call.

## Monitors

deadlock in semaphores used in P-C problem.

Monitor: a special kind module (a collection of procedures, variables, and data structures)

Compiler will implement the mutual exclusion

Introduction of Condition Variable

## Message Passing

### Design Issues for mesage Passing system

+ signal lost: acknowledgement
+ acknowledge signal lost: 
+ authentication

### The Producer-Consumer Problem with Message Passing

+ buffered:mailbox
+ no buffering: rendezvous

## Barriers

synchronization mechanism for groups of processes

# classical IPC Problems

## The Dining Philosophers Problem

Modeling process that are competing for exclusive access to a limited number of resources.

## The Reader and Writer Problem

modeling access to a database

## The Sleeping Barber Problem

queueing situation

# Scheduling

## Introduction to Scheduling

Difference between PC and networked workstation

### Process Behavior

+ Compute-bound
+ I/o-bound

As CPUs get faster, processes tend to get more I/O-bound.

### When to Schdule

+ New Process is created
+ process exits
+ process blocks
+ I/O Interrupt: nonpreemptive/preemptive

### Catagories of Scheduling Algorithms

+ Batch
+ Interactive
+ Real Time

### Scheduling Algorithm Goals

+ All Systems
  + Fairness
  + Policy enforcement
  + balance
+ Batch Systems
  + throughput - maximize jobs per hour
  + turnaround time - minimize time between submission and termination
  + CPU utilization - keep the CPU busy all the time
+ Interactive systems
  + response time
  + proportionality
+ Real-time system
  + Meeting deadlines
  + predictability

## Scheduling in Batch Systems

### First-Come First-Served
Advantages:
+ easy
+ fair

Disadvantages:
+ bad performance 

### Shortest Job First

Optimal when the jobs arrives simultaneously

### Shortest Remaining Time Next

Preemptive version of Shortest Job First Algorithms

### Three-Level Scheduling

+ Admission Scheduler
+ CPU Scheduler
+ Memory Scheduler

## Scheduling in Interactive System

### Round-Robin Scheduling

time interval: **quantum**

+ Short quantum: process switch, low efficiency
+ High quantum: poor response time

### Priority Scheduling

Statically assigned Priority

Dynamically assgined Prority:
    Set the priority of the I/O bounded process: 1/f

### Multiple Queues

Reducing the swap: give large quantum

Priority classes

### Shortest Process Next

How to estimate the run time of the process?

Based on past behavior.

### Guaranteed Scheduling

Each process can get a fair guarantted CPU cycle

### Lottery Scheduling

### Fair-Share Scheduling

## Scheduling in Real-Time System

+ Hard Real-time
+ Soft Real-time

Event Category:
+ Periodic
+ aperiodic

The definiction of Schedulable: 

## Policy versus Mechanism

scheduling mechanism
scheduling policy: set by the children

## Thread Scheduling

+ User-level
  + Kernel picks a process
  + Runtime system picks a thread
+ Kernel-level
  + Kernel picks a thread

Comparison:

+ Performance: full context switch vs. handful of machine instructions
+ I/O block: user level thread will block o I/O
+ user-level applocation-specific thread scheduler










