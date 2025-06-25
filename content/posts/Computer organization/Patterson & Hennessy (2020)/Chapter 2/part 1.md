---
title: "Part 1: Introduction"
draft: true
---
The book uses top-down method, where they start from a notation that resembles some low level programming language and break it down until it is using the language of a real computer.

Following this comparison, we can say *instructions* are the words and *instruction set* is the vocabulary that computers use.

The instruction set (vocabulary) the authors chose for the book was RISC-V. But unlike humans, computer languages aren't as diverse. So, learning another instruction set is much easier than say learning French.

To demonstrate this, the book also demonstrates MIPS and Intel x86 instruction sets. 

The common goal for hardware design: increase performance, decrease cost and energy.

Stored-program concept: The idea that instructions and data of many types can be stored in memory as numbers and thus be easy to change, leading to the stored-program computer.

Each RISC-V arithmetic instruction performs one operation and have 3 variables.
Each line can contain at most one instruction.
Requiring every instruction to have exactly three operands, no more and no less, conforms to the philosophy of keeping the hardware simple: hardware for a variable number of operands is more complicated than hardware for a fixed number.

>**Design Principle 1:**
>Simplicity favors regularity

