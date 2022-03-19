---
id: 02-memory-management
title: Memory Management
tags:
  - Unity
  - Design
  - Patterns
  - Performance
  - Memory
  - Management
---

## Introduction

The basic philosophy is to minimise garbage collection. Garbage collection results in the CPU running instructions outside of the execution of your scripts. The more this happens, the less time you have each frame to execute your logic.

## Memory Organisation

### Heap

The heap is an area of memory allocated to a class when it is instantiated. Instance variables are stored on the heap.

When a class is disposed, the memory on the heap for the class is freed.

### Stack

The stack is a region of memory "assigned" to a method, or function when the method is called. This is memory that was allocated when the application starts, so doesn't get allocated again while the application is running.

The stack pointer for the CPU points to the stop of the stack.

When a method is called, and the method has arguments, the compiler will generate code that may push some register values to the stack before calling, in order to preserve their values, and may push some of the arguments to the method onto the stack as well.

When the method returns, the compiler generates code to pop values off the stack. If the method returns a value, this value may be one of the values that are popped off the stack as well.

### Data Packing

The C# compiler does a pretty good job of organising variables in memory. It is possible however, to take over this responsibility, but its not recommended unless you have good reason.

The compiler will generally re-arrange your variables in memory during compilation. This will ensure the data is packed optimally.

The CPU access data quicker when the data is aligned to certain values. A 64bit CPU will access data in blocks of 64bits. If our data is aligned to the same 64bit boundaries, the CPU can read 1 64bit value into memory, or 2 32bit values into memory, in one go.

If the data spans a 64bit boundary, the CPU will take longer to load the data into memory.

When the compiler arranges data, it tries to ensure that data of the same type and size is located next to each other. This way there are no gaps in the memory.

If there are gaps, the CPU ends up reading more memory to get to the data. If there are no gaps, the CPU is able to read less memory.

This also helps because more data can be stored in the CPU's cache, which means less cache misses, and less trips to slower memory.



## Garbage Collection Tactics

### Suitable Points To Free Memory

### IDispose Interface

## Object Pooling

## Lists vs Arrays vs Linked Lists
