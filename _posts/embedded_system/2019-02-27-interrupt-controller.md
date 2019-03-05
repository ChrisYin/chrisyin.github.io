---
layout: post
title:  "interrupt controller abstract model and its layer structure"
date:   2019-02-28
categories: embedded system
---

Interrupt controller is used to collect interrupts and send them to their handlers. When implementing hyperviosr in Raspberry Pi3, I did some work to emulate its special interrupt controller. Now, I want to conclude a general interrupt controller model which can be used in formal verfication. And this model should work well both in ARM and x86 architecture.

# ARM 

## Generic Interrupt Controller(GIC)
A common interrupt controller programming interface applicable to uniprocessor or multiprocessor systems.

interrupt sources/ interrupt behavior/ interrupt routing

### Terminology

+ interrupt states

	+ inactive
	+ pending: waiting to be serviced
	+ active: has been acknowledged and has not completed.
	+ active and pending: 
	
+ interrupt types:

	+ peripheral interrupt
	
		+ Private Peripheral Interrupt
		
		+ Shared Peripheral Interrupt
		
			+ Edge-triggered
		
			+ Level-sensitive
		
		+ Software-generated interrupt: edge-triggered
		
		+ Virtual interrupt
		
		+ Maintenance interrupt: level-sensitive

### GIC partitioning

+ Distributor: GICD_

+ CPU interfaces: GICC_

+ virtual CPU interfaces

### The Distributor

interface:

+ enabling or disabling each interrupt
+ setting the priority level
+ setting interrupt type

### CPU interfaces

interface:

+ acknowledging an interrupt
+ indicating completion of the processing of an interrupt

### Interrupt Handling and Prioritization

+ identifying the supported interrupts
  
  + reading the GICD_TYPER to get the IRQ number
  + writing to the GICD_CTLR to disable forwarding of interrupts from the distributor to the CPU interface
  + writing GICD_ISENABLERn/and read
  
#### General handling of interrupts

sequence:

+ The GIC determines the interrupts that are enabled. An interrupt that is not enabled has no effect on the GIC.

+ The GIC determines the targeted processor

+ The distributor forwards the highest priority pending interrupt that targets the interface.

+ Each CPU interface determines whether to signal an interrupt request to its processor according its priority.

+ The processor acknowledges the interrupt(reading the GICC_IAR of its CPU interface), and the GIC returns the interrupt ID and updates the interrupt states. 
  
	  + pending -> active
	  + pending -> active and pending.

+ After processing the interrupt, the processor signals EOI of the GIC. If, after the EOIR write(prioirty drop and interrupt deacitivation), there is no pending interrupt of Sufficient priority, the CPU interface deasserts the interrupt exception request to the processor.

#### Interrupt controls in the GIC

+ interrupt enables

+ setting and clearing pending state of an interrupt

+ Finding the active or pending state of an interrupt

+ generating an SGI

#### Interrupt handling state machine

#### Interrupt prioritization

+ preemption
+ priority masking: CPU interface defines a priority threshold
+ priority grouping

## Pseudocode details of interrupt handling




## Raspberry Pi Interrupt Controller

### Introduction

+ sources:
  
  + from ARM specific peripherals: level sensitive(remain asserted until disabled or the interrupt source is cleared)
  + from GPU peripherals
  + special events interrupts
  
+ registers:

  + interrupt enable bit
  + interrupt pending bit(read only)

### interrupt priority

There is no priority for any interrupt.



### Sequence:

1. Configuration:

	+ initialization: 


### BCM2836 interrupt controller

# x86

## External Interrupt

+ local APIC:
  
  IO APIC's pins can be directed to the local APIC through system bus.

+ INTR pins: external interrupt controller

## Software-generated Interrupt

using INT *n* instruction.

## Sources of exceptions

## Enabling and Disabling Interrupts

## Interrupt Handling



## Programmable Interrupt Controller(PIC)

Five hardware interrupts.

register:

+ IRR: Interrupt Request Register
  
  interrupt level which are requesting for interrupt services
  
+ ISR: Interrupt Service Register

  interrupt level which are currently being executed.
  
+ IMR: Interrupt Mask Register

  interrupt level which have to be masked by storing the mask bit.

## I/O APIC

### Enabling or Disabling the local APIC

### Handling Local interrupts




