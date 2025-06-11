---
title: "Part 4: Real-World Examples & Wrap-Up"
tags:
  - calas
  - computer_architecture
  - risc-v
  - theory
weight: "4"
draft: false
---
## Benchmarking the Intel Core i7

### SPEC CPU Benchmark

If you had 2 computers, how would you know one of them performed better than the other? Whichever computer that completes the task faster is the better computer. But to make it a fair competition, you would have to see which one performs better on the same **workload**.

The various programs used to test the performance is called **benchmarks**. As mentioned in "[The 8 Great Ideas in Computer Architecture](/posts/computer-organization/notes/patterson--hennessy-2020/part-1/)", to make the **common case** fast, we need to know what the common case is.

One benchmark introduced by computer vendors is *System Performance Evaluation Cooperative* (**SPEC**). It has 12 integer benchmarks and 17 floating point benchmarks. 

>The integer benchmarks go from C compiler to chess engine to Quantum simulation. The floating point benchmarks include structured grid codes for finite element modeling, particle method codes, to sparce linear algebra codes.

To make it easier for making comparisons, we use **SPECratio**. 
$$
SPEC Ratio = \frac{\text{Measured Time}}{ \text{Reference Time}}​
$$
This gives individual performance metric for each of the programs in SPEC benchmark. We can then take the geometric mean of the ratios.
$$
GeoMean=(∏_{i=1}^n​SPEC Ratio_i​)^{1/n}
$$

This geometric mean is used because it produces the same result regardless of the computer that was used as the reference.

### SPEC Power Benchmark

The power benchmark was added later after it became apparent how important power consumption was.

In the **SPECpower benchmark, the energy efficiency of a server is measured by the number of server-side Java operations performed per watt of power consumed.

The system is tested at 11 load levels (from 0% to 100% in 10% increments). 
The `ssj_ops/watt` score is computed by summing the performance across all load levels and dividing by the total average power:

$$
\text{ssj\_ops/watt} = \frac{
\sum_{i=0}^{10} \text{ssj\_ops}\_i
}{
\sum_{i=0}^{10} \text{power}\_i
}
$$

Where:

- $\text{ssj\_ops}\_i$: Average server-side Java operations per second at load level $i$
- $\text{power}\_i$: Average power in watts at load level $i$
- $i = 0, 1, 2, ..., 10$: Corresponding to 0% through 100% load levels

It measures processors, caches, main memory as well as Java virtual machine, compiler, garbage collector, and pieces of operating system.
## Concluding Remarks

This part concluded the chapter again bringing attention to the 8 great ideas, evaluating the performance of computers, current constraints and elaborated on the 5 classic components of the computer and how they serve as a framework for the rest of the book.

Chapter 3: Datapath

Chapter 4: Datapath, Control (what we also call processor)

Chapter 5: Memory, Input, Output

Chapter 6: Datapath, Control, Input, Output

Appendix B: Datapath, Control

I would like to formally end the summary for Chapter 1 with a quote mentioned in the book by **Alfred North Whitehead** in his 1911 book _"An Introduction to Mathematics."_

> “Civilization advances by extending the number of important operations which we can perform without thinking about them”



___
References:
Hennessy, J. L., & Patterson, D. A. (2018). _Computer Organization and Design: RISC-V Edition_ (2nd ed.). Morgan Kaufmann/Elsevier.
