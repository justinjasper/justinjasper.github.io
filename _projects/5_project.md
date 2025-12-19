---
layout: page
title: Custom Heap Allocator
description: Designed and implemented a custom heap allocator in C, featuring both implicit and explicit free lists for dynamic memory allocation.
img: assets/img/heap_screenshot.png
importance: 3
category: Systems Programming
---

I developed this project as part of my Stanford coursework in CS107: Computer Organization & Systems.

This assignment gave me the opportunity to implement a core piece of functionality that I had relied on throughout the quarter: a heap allocator. The project involved building my own version of `malloc`, `realloc`, and `free` from scratch, going under the hood to understand how dynamic memory allocation actually works.

## Key Goals

The implementation focused on three critical objectives:

- **Correctness**: The allocator must service any combination of well-formed requests without errors
- **Tight Utilization**: Compact use of memory with low overhead and effective memory recycling
- **Speed**: Fast request servicing with minimal latency

These goals presented interesting tradeoffs. A bump allocator can be extremely fast but uses memory inefficiently, while an allocator focused on aggressive memory recycling might achieve excellent space utilization at the cost of execution speed. The challenge was finding the right balance.

## Implementation

I implemented two different heap allocator designs:

**Implicit Free List Allocator**: This design uses a single implicit list where free blocks are identified by traversing the entire heap. While simpler to implement, this approach requires more time to find suitable free blocks.

**Explicit Free List Allocator**: This design maintains explicit pointers between free blocks, creating a linked list structure that allows for faster allocation and deallocation operations. This design required careful management of pointer updates during coalescing operations.

Both implementations required careful handling of block headers, boundary tags, and coalescing strategies to efficiently manage memory fragmentation. I experimented with different approaches for finding and allocating blocks (algorithmically balancing between first-fit and best-fit) and worked to optimize the tradeoffs between memory utilization and allocation speed.

This experience deepened my understanding of low-level memory management and the complexity that lies beneath the interface of `malloc` and `free`.
