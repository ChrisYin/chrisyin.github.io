---
layout: post
title:  "Chapter3: Deadlocks"
date:   2019-06-24
categories: Modern Operating System
---

Chapter Three: Deadlocks

# Resources

## Preemptable and Nonpreemptable Resources

In general, deadlocks involve nonpreemptable resources.

## Resource Acquisition

+ Using semaphores.
+ order of resource acuisition can lead deadlock

# Introduction to deadlock

Deadlocked processes are waiting for a resource that is owned by a deadlocked process.

### Conditions for deadlock

+ mutual exclusion condition
+ hold and wait condition
+ no preemption condition
+ circular wait condition

### Deadlock Modeling

resource allocation graph

four stategies:
+ just ignore the problem
+ detection and recovery
+ dynamic avoidance
+ prevention: negating four conditions

# The ostrich algorithm

Just ignore the problem, because it rarely happens.

# Deadlock detection and recovery

## Deadlock detection with one resource of each type

Brute force to go through every node.

## Deadlock Detection with Multiple Resource of Each Type

Using matrix to detect

## Recovery from deadlock

### Recovery through Preemption

is hightly dependent on the nature of the resources

### Recovery through rollback
 
Create checkpoint for each process

### Recovery through Killing Processes

# Deadlock Avoidance

## Resource Trajectories

Example: two processes and two kinds of resources

## Safe and Unsafe States

from a safe state the system can guarantee that all processes will finish; from an unsafe state, no such guarantee can be given.

## The Banker's ALgorithm for Single Resource

See if granting it leads to a safe state

## The Banker's Algorithm for Multiple Resources

The same as single resource

# Deadlock Prevention

Deadlock avoidance needs information about future requests.

## Attacking the mutual exclusion condition

## Attacking the Hold and Wait Condition

## Attacking the No Preemption Condition

## Attacking the Circular Wait COndition












