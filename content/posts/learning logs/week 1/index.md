---
title: Week 1
date: 2025-05-19
showTableOfContents: true
tags:
  - calas
  - learning_log
showHeadingAnchors: true
---
## Week 1 Learning Log (May 19–23, 2025)

### 1. Objectives
- Grasp FPGA internal architecture: CLBs, LUTs, and on-chip SRAM/Block RAM   
- Install and configure Vivado/Vitis on Windows 
- Implement and simulate basic arithmetic primitives:  
  - **Half Adder** (`half_adder.v`)  
  - **Full Adder** (`full_adder.v`)  
  - **4-bit Carry Propagation Adder** (`prop_adder`)  

### 2. Daily Activities

#### 📅 Mon, May 19

- Reviewed FPGA architecture:  
    _CLB = LUT + multiplexer + flip-flops + block RAM (SRAM-based)_  
    Also looked at programmable interconnects.
    
- Created internship timeline
    

#### 📅 Tue, May 20

- Downloaded and ran **AMD Unified Installer** (Vivado & Vitis 2022.2)
    
- Configured WebPACK license and environment
    

#### 📅 Wed, May 21

- Wrote `half_adder.v` and testbench `Half_Adder_tb.v`
    
- Ran behavioral simulation in **XSim** to verify sum/carry truth table
    

#### 📅 Thu, May 22

- Imported `half_adder` into new project
    
- Added `full_adder.v` and `Full_Adder_tb.v`
    
- Simulated full-adder behavior
    
- Extended to 4-bit `prop_adder` using **IP Integrator**
    

#### 📅 Fri, May 23

- Ran synthesis for all designs
    
- Analyzed LUT utilization and CLB mapping
    
- Wrote blog posts on:
    
    - **SRAMs** (how cells store truth tables)
        
    - **Bistable Flip-Flops**
        
    - **LUTs**

### 3. Key Learnings
- **Configurable Logic Block (CLB):** core building block comprising LUTs, muxes, flip-flops for implementing user logic 
- **Look-Up Tables (LUTs):** small SRAM-based memory (e.g., 4- to 6-input) that encodes combinational logic; viewed utilization post-synthesis 
- **Block RAM (SRAM):** larger on-chip SRAM blocks for data storage/state machines within designs 
- **Vivado Flow:** project setup → HDL source & test-bench creation → simulation (XSim) → synthesis/implementation → bitstream generation 
- **Arithmetic Modules:**  
  - **Half Adder:** `sum = a ^ b`, `carry = a & b`  
  - **Full Adder:** cascaded half-adders with carry-in/out  
  - **4-bit Carry Propagation Adder:** chain of four full-adder blocks (`prop_adder`) 

### 4. Next Steps (Week 2)
1. Test hardware on Zedboard: program bitstreams for half, full, and `prop_adder` designs  
2. Dive into Vivado IP Integrator: automate block-design for multi-bit adders  
3. Begin drafting a simple ALU control module and integrate adders
