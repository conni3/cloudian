---
draft: true
title: "Part 1: Foundations & “Eight Great Ideas”"
tags:
  - computer_architecture
  - calas
  - theory
  - risc-v
weight: "1"
---
# Preface

The preface starts with a motivation to read this book - *professionals of every computing specialty should understand both hardware and software*. This point was emphasized when the authors mentioned the switch from <u>uniprocessor to multicore microprocessors</u> (which will be emphasized many more times throughout Chapter 1). Until tools (and researchers) can fully hide the parallel nature of today’s hardware, programmers must have at least a basic understanding of both hardware and software to write high-performance code.

The book uses **RISC-V ISA**, the instruction set the authors invented to explain computer architecture - <u>which takes advantages of the elegance of MIPS intruction set while cleaning up its "quirks"</u>.

# Chapter 1

The first chapter focuses on giving the readers <u>basic understanding of the architecture</u>, namely some keywords that will be used in the later sections. This was delivered with the *context of past and current developments*, *design challenges, real-life examples* while layering up the concepts in a seamless way. Another thing to add is that the book asks, or delivers information in a very thought provoking manner. There were many moments when I got lost in thought or were stuck in a dilemma to go on a "google/gpt spiral" or to continue reading the book.

## Introduction

First section of the chapter introduction - gets the reader familiar with classes of computers, with emphasis on PMDs exceeding PC usage in the *post-PC era* and lightly mentions the *constraints* of computer architecture over the years. The constraints evolved from size of computer's memory to parallel nature of processors and hierarchical nature of memories (which improved the performance of a C program by a factor of 200) and our most recent challenge - the power wall (which is explained in later sections).

> “Today’s science fiction suggests tomorrow’s killer applications: already on their way are glasses that augment reality, the cashless society, and cars that can drive themselves.”

This was a quote I found interesting and somewhat humorous. The book was written in 2019 and the "science fiction" then now has already become a reality.
## The 8 great ideas in Computer Architecture
### Moore's law

According to Moore's law, the number of transistors in IC (integrated circuit) will double every 2 years. This has been true over 50 years, although there has been some fluctuations. Therefore, a computer architect should always design their architecture based on how the industry will be when their work is done.
### Abstraction

Abstraction is another idea that helps hardware and software designers work more efficiently. The main idea is that each layer abstracts away the lower layer, essentially hides them idea. This is done at every level. Even in simple circuit analysis, components and parts of the circuit are replaced with a "box" with input and output.
### Making the common case fast

It is often easier to make the common case faster than the rare case. And simpler to do so too. 
### Performance via Parallelism

Parallelism is heavily mentioned in the book (at least in the introduction and the first chapter). Idea is more people working on something, the faster it will be. 

One noteworthy thing is the idea of parallelism came when scaling a single processor (by packing more transistors to it) reached its limits (due to constraints we will explore in [here](/posts/computer-organization/notes/patterson--hennessy-2020/part-3the-power-wall/))

### Performance via Pipelining

Pipelining - this can be understood by how a factory works. Every part does one specific thing and then passes it on to another part. At every stage, a single simple action is done. Simpler, repetitive means each step takes smaller time and has less error.
### Prediction

The quote I really liked was here was "It can be better to ask for forgiveness than to ask for permission, the next great idea is prediction". One of the ideas that helped accelerate computing was prediction - assuming if you make a wrong prediction, you can recover from it with quickly.
### Memory Hierarchy

Finally, the memory hierarchy. People often think that accessing data on memory takes constant time. And that is the brilliance of what the earlier architects have accomplished. **In reality, memory is composed of multiple types of memory - what we call "the memory hierarchy"**

It looks like a pyramid. The one at the top is the smallest - faster, more expensive. The one at the bottom is the largest - slower, but cheaper. By the clever tricks employed by the designers, we, the users think that memory is as fast as the one on top, and as cheap as the one on the bottom. 

### Dependability by Redundancy

There are components in a computer that adds dependability (in case of a failure). This is a trade-off in performance, however, makes the system resilient to crashes or data loss.

___
This is the end of the first part, please read the other parts for the book or any article you find interesting :D

References:
Hennessy, J. L., & Patterson, D. A. (2018). _Computer Organization and Design: RISC-V Edition_ (2nd ed.). Morgan Kaufmann/Elsevier.