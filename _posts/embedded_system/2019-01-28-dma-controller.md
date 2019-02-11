---
layout: post
title:  "dma controller in Raspberry Pi3"
date:   2019-01-27
categories: embedded system
---

Recently, I'm working on device emulation in Raspberry Pi3. Emulating the dma controller needs a lot of work. I decide to passthrough the dma controller to the virtual machine while keeping the security of the whole system. I will add a monitor between the VM and the real dma controller to filter error memory access.

# what is dma controller

> Direct memory access (DMA) is a feature of computer systems that allows certain hardware subsystems to access main system memory (random-access memory), independent of the central processing unit (CPU).

Many external devices will use dma to access memory to get a beteer performance. DMA can also used for memory to memory copying or moving data.

# dma controller in BCM2835(Pi3)

+ Pi3 provides a total of 16 dma channels.

+ Each DMA channel operates by loading a control block data structure from memory to internal registers. 

+ Each CB can point to the next CB, as a linked list does.

+ control block data structure
	
  - Transfer Infomation: TI reg
  - Source Address: source_ad reg
  - Destination Address: dest_ad reg
  - Trasfer Length: txfr_len reg
  - 2D Mode Stride: stride reg
  - Next Control Block Address: nextconl reg
  - Reserved:
  
+ register map
  only CS/conblk_ad/debug can be set directly. Other register are loaded from a control block.
  
  - CS
  - conblk_ad
  - TI
  - source_ad
  - dest_ad
  - txfr_len
  - stride
  - nextconbl
  - debug

# dma passthrough: security aspect

  check the source\_ad and dest\_ad register.
