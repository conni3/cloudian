---
title: Internship Timeline
date: 2025-05-20
tags:
  - learning_log
  - calas
showDate: true
showTaxonomies: true
showTableOfContents: true
showSummary: true
---
## Motivation for the internship:

In the long term future, I really want to become a researcher in the future. It might come from trying to be enough or even feel better. But I really do want to become someone I can be proud of and someone who grows everyday. 

This might be a bit of a rocky road and I keep hearing that from a lot of people and sometimes I get scared, but there are also people who support me. So I am willing to give it a try.

Back to the topic of this internship specifically, the main goal is that I build a processor.

Here is what I am hoping to gain from doing that:
- Although I had the digital logic circuit class, I have noticed that I have forgotten a lot of the materials in a little over semester. This made me quite sad. All in all, will review FPGAs.
- Would like to learn computer architecture. I haven't taken a computer architecture or organization course yet (core course in the degree but an elective, which is very odd since I am doing a computer engineering degree)

---
## Timeline

### Weeks 1-3 FPGA design 

#### Week 1: Environment & Basics
- Setting up Vitis 
- Review Verilog syntax and some combinational circuits
- Building testbench for simulation

#### Week 2: Core modules
- Design and verify an n-bit ALU (add, subtract and logic operations)
- Implement a simple register file
- Integrate ALU + simple register file

#### Week 3: Synthesis and Testing on board
- Synthesize the design on PYNQ-Z2
- Write constraints
- Load the bitstream and run I/O tests
- Document timing results and resource utilization

---
### Weeks 4-6 Computer architecture

#### Week 4: Instruction set architecture
- Read up on ISA concepts (RISC vs CISC, datapath components)
- Explore the RISC-V base spec
- Draw a simplified datapath diagram

#### Week 5: Pipelining & Control
- Learn pipeline stages and hazards
- Simulate a 5-stage pipeline in software 
- Implement hazard detection & forwarding logic on paper

#### Week 6: Memory & I/O
- Study memory hierarchy (registers, cache, main memory)
- Model a cache in simulation (measure hit/miss rates)
- Review basic I/O interfacing (memory vs port mapped)

---
### Weeks 7-9 Implementing RISC V architecture
#### Week 7: Core Integer Pipeline
- Translate the simulated pipeline into HDL modules
- Implement fetch-decode-execute stages in Verilog

#### Week 8: Completing the Pipeline
- Add MEM and WB stages; integrate control signals
- Test a small instruction sequence on the FPGA

#### Week 9: Extensions and Testing
- Implement branches and simple control/status registers
- Develop a test suite
- Measure and document performance

___
### Weeks 10-12 Improvement and Further Research

#### Week 10: Optimization
- Add hazard reduction features (branch prediction, deeper pipelines)
- Profile performance improvements

#### Week 11: Advanced Features
- Explore floating-point or vector extensions
- Prototype an exception/interrupt handler

#### Week 12: Documentation and Demo
- Prepare a design report
- Recording a demo of the processor
- Identify open questions for future work

