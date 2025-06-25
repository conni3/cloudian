---
title: Internship Timeline
date: 2025-05-20
tags:
  - learning_log
  - calas
showDate: false
showTaxonomies: false
showTableOfContents: true
showSummary: true
showHeadingAnchors: true
---
## Motivation for the Internship:

I am passionate about forging a career in research and innovation within computer engineering. This internship offers a unique opportunity to translate my theoretical knowledge into hands-on expertise by designing and building a processor from the ground up. 

<!--more-->

Though I’ve enjoyed studying digital logic circuits, I’ve noticed that much of what I learned has faded over time—and I’m determined to refresh and deepen those fundamentals.

Beyond simply revisiting FPGA workflows, I’m excited to explore computer architecture in depth—an area I haven’t yet had formal coursework in, despite it being central to my degree. By guiding a design through every stage—from HDL simulation to on-board testing—I aim to:

- Master FPGA toolchains and digital-logic design
	
- Build a solid understanding of RISC-V instruction set and datapath organization
	
- Bridge the gap between abstract concepts and real hardware implementation
	
- Cultivate the confidence and skills I need to grow each day as a researcher

Ultimately, I believe this hands-on experience will be the cornerstone of my journey toward becoming the kind of engineer and researcher I aspire to be.

---
## Timeline

### Weeks 1-3 FPGA Design

#### Week 1: Environment & Basics
- Setting up Vitis 
- Review Verilog syntax and some combinational circuits
- Building testbench for simulation

#### Week 2: Core Modules
- Design and verify an n-bit ALU (add, subtract and logic operations)
- Implement a simple register file
- Integrate ALU + simple register file

#### Week 3: Synthesis and Testing on Board
- Synthesize the design on PYNQ-Z2
- Write constraints
- Load the bitstream and run I/O tests
- Document timing results and resource utilization

---
### Weeks 4-6 Computer Architecture

#### Week 4: Instruction Set Architecture
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
### Weeks 7-9 Implementing RISC V Architecture
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

