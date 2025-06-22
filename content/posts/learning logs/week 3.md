---
tags:
  - calas
  - learning_log
title: Week 3
showSummary: true
summary: 
date: 2025-06-06
---
## Week 3 Learning Log (June 2–6, 2025)
### 1. Objectives
- **ALU Implementation & Testing**  
  - Design a simple 4-bit ALU using Vivado IP Integrator arithmetic blocks (`alu_bd.v`)  
  - Verify functionality via testbench and hardware simulation
- **FPGA Design Flow**  
  - Meet with Sanka to review end-to-end FPGA design flow (synthesis, implementation, place-and-route)

- **Reading & Blogging**  
  - Read **Patterson & Hennessy, Chapter 1 (“Computer Abstractions and Technology”)**  
  - Write blog posts summarizing Chapter 1 divided into four thematic sections:
    1. **Foundations & The Eight Great Ideas**  
    2. **Inside the Machine – Abstraction Layers & Technologies**  
    3. **Performance, Power & the “Sea Change”**  
    4. **Real-World Examples & Wrap-Up**
- **Lab Session**  
  - Attend the Edge AIoT and Microelectronics TA session to receive training, lab components and complete assigned lab

---

### 2. Daily Activities

#### 📅 Monday, June 2
- **4-bit ALU via IP Integrator**  
  - Opened a new Vivado project.  
  - Launched IP Integrator: instantiated Xilinx “Arithmetic & Logic” IP (configured for 4-bit width).  
  - Wired up inputs:  
    - A[3:0], B[3:0] ports  
    - op[2:0] to select ADD, SUB, MULTIPLY, DIVIDE  
  - Added constant generator blocks to drive OpSel and tested all combinations.  
  - Generated Block Design wrapper and created `alu_bd.v` top-level module.  
- **Testbench & Simulation**  
  - Wrote `alu_tb.v` to sweep A/B values and check results for each op value.  
  - Ran behavioral simulation in XSim; verified:  
    - ADD: correct sum and carry-out  
    - SUB: correct two’s-complement difference and borrow flag  
    - MULTIPLY: correct product
    - DIVIDE: correct quotient and remainder

#### 📅 Tuesday, June 3
- **Reading: P&H Chapter 1, Section 1 (“Foundations & The Eight Great Ideas”)**  
  - Covered motivation for studying computer architecture and the shift from uniprocessor to multicore. 
  - Identified the eight design principles:  
    1. Abstraction  
    2. Pipelining  
    3. Parallelism  
    4. Prediction  
    5. Memory Hierarchy  
    6. Hierarchical Protection  
    7. Reliability  
    8. Energy Efficiency  
  - Took detailed notes on how each principle recurs in modern CPU/SoC design.  

- **Blog Drafting: Section 1**  
  - Drafted “Foundations & The Eight Great Ideas”:  
    - Motivation for performance (Moore’s Law slowing)  
    - Core principles that transcend specific technologies  
    - Examples: how pipelining and parallelism appear in multicore CPUs

#### 📅 Wednesday, June 4
- **Meeting with Sanka – FPGA Design Flow Review**  
  - Discussed steps from RTL → synthesis → implementation → place-and-route → timing closure → bitstream generation  

- **Edge AIoT & Microelectronics TA Session**  
  - Attended the TA training lab:  
    - Received training on Fundamentals of Microelectronics and Digital Systems Design
    - Received lab components (breadboard, transistors, resistors, wiring)  
    - Completed initial lab
- **Reading: P&H Chapter 1, Section 2 (“Inside the Machine – Abstraction Layers & Technologies”)**  
  - Explored layers from high-level code down to transistors: ISA, microarchitecture, logic, devices, circuits  
  - Reviewed core technologies: static CMOS, SRAM, DRAM, interconnect fabrics  
- **Blog Drafting: Section 2**  
  - Drafted “Inside the Machine – Abstraction Layers & Technologies”:  

#### 📅 Thursday, June 5
- **Reading: P&H Chapter 1, Section 3 (“Performance, Power & the ‘Sea Change’”)**  
  - Learned performance metrics: CPI (cycles per instruction), instruction count, clock rate  
  - Reviewed Amdahl’s Law and its implications for parallelism  
  - Understood power constraints: the Power Wall, Dark Silicon, and energy efficiency trends  
- **Blog Drafting: Section 3**  
  - Drafted “Performance, Power & the ‘Sea Change’”:  
    - How to calculate CPU performance using CPI×IC×ClkPeriod  
    - Why single-threaded frequency scaling plateaued, necessitating multicore  
    - Introduction to power-performance trade-offs and dynamic voltage/frequency scaling (DVFS)

#### 📅 Friday, June 6
- **Reading: P&H Chapter 1, Section 4 (“Real-World Examples & Wrap-Up”)**  
  - Examined Intel Core i7 benchmark analysis: how the eight ideas appear in a commercial CPU  
  - Reviewed common fallacies (e.g., “faster clock always wins”) and pitfalls (e.g., ignoring memory latency)  
  - Identified the five classic components of a computer:  
    1. Processing Unit  
    2. Memory Unit  
    3. I/O Unit  
    4. Network/Interconnect  
    5. Storage  
- **Blog Drafting: Section 4**  
  - Drafted “Real-World Examples & Wrap-Up”:  
    - Applied principles (pipelining, caching) to Intel Core i7 data  
    - Summarized the five components as a roadmap for the rest of the book  
- **Documentation & Website Updates**  
  - Uploaded `alu_tb.v`, testbench, and waveform captures to Hugo site  
  - Wrote Week 3 blog posts for all four sections: Foundations, Abstractions, Performance & Power, Examples & Wrap-Up  
- 

---

### 3. Key Learnings
- **4-bit ALU via IP Integrator**  
  - Leveraged Xilinx arithmetic IP to build ADD, SUB, AND, OR, XOR operations in one block  
  - Verified that IP Integrator correctly generated ports and constraints; saw how the block maps to LUTs/FFs  
- **FPGA Design Flow**  
  - Understood the complete Vivado flow from RTL to bitstream, including critical constraint and timing steps  
- **P&H Chapter 1 Highlights**  
  - **Foundations & Eight Great Ideas**: Core principles (abstraction, pipelining, parallelism, memory hierarchy, etc.) form the basis of all architectures  
  - **Abstraction Layers**: How high-level software ultimately relies on transistor-level implementations; importance of mapping optimizations across layers  
  - **Performance & Power**: Metrics (CPI, instruction count, clock rate), Amdahl’s Law, and power-limited scaling leading to multicore designs  
  - **Real-World Examples**: Intel Core i7 data shows lessons in pipelining, caching, and parallel thread execution; five classic components framework guides subsequent chapters

---
