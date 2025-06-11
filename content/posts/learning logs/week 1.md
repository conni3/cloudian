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
- **FPGA Architecture & Tools**  
  - Understand FPGA internal architecture: CLBs (LUTs, muxes, flip-flops), on-chip SRAM/Block RAM  
  - Install and configure Vivado/Vitis 2022.2 on Windows  
- **HDL Implementation & Simulation**  
  - Implement and simulate basic arithmetic primitives:  
    - Half Adder (`half_adder.v`)  
    - Full Adder (`full_adder.v`)  
    - 4-bit Ripple Carry Adder (`prop_adder.v`)  
- **Reading & Documentation**  
  - Read and reviewed Combinational Logic lectures from EE2000
  - Draft concise write-ups on SRAM cell operation, bistable flip-flops, and LUT fundamentals 

---

### 2. Daily Activities

#### 📅 Monday, May 19
- **FPGA Architecture Overview**  
  - Studied CLB internals: each CLB contains LUTs backed by SRAM bits, local multiplexers, and flip-flops 
  - Reviewed Block RAM (SRAM-based) structure: how 6-T SRAM cells store truth tables and provide synchronous read/write
  - Explored programmable interconnect fabric: how CLBs interconnect via switch matrices.  
- **Planner & Timeline**  
  - Created a high-level internship timeline, aligning Weeks 1–12 with incremental HDL targets and chapter readings.

#### 📅 Tuesday, May 20
- **Vivado/Vitis Installation**  
  - Downloaded and ran **AMD Unified Installer 2022.2** (includes Vivado and Vitis)
  - Configured WebPACK license; confirmed license activation within Vivado.  
  - Set up environment variables and verified `vivado –version` and `vitis –version` on Windows.  

#### 📅 Wednesday, May 21
- **Half Adder Implementation**  
  - Wrote `half_adder.v`:  
    ```verilog
    module half_adder (input  a, b,
                       output sum, carry);
      assign sum   = a ^ b;
      assign carry = a & b;
    endmodule
    ```  
  - Created testbench `Half_Adder_tb.v`; applied all four (a,b) combinations.  
  - Ran behavioral simulation in **XSim**; verified truth-table matches expected sum/carry outputs.  
- **Reading**  
  - Read fundamentals of gates, combinational logic, half-adder/full-adder
  - Read implementation details for `sum = a ⊕ b`, `carry = a ∧ b` ().

#### 📅 Thursday, May 22
- **Full Adder & 4-bit Ripple Carry Adder**  
  - Imported `half_adder.v` into a new Vivado RTL project.  
  - Developed `full_adder.v` by cascading two half-adders plus an OR gate:  
    ```verilog
    module full_adder (input  a, b, cin,
                       output sum, cout);
      wire s1, c1, c2;
      half_adder ha0 (.a(a), .b(b),  .sum(s1), .carry(c1));
      half_adder ha1 (.a(s1),.b(cin),.sum(sum),.carry(c2));
      assign cout = c1 | c2;
    endmodule
    ```  
  - Created `Full_Adder_tb.v`; applied all eight (a,b,cin) vectors in XSim to verify sum/ cout.  
  - Extended to 4-bit ripple carry adder (`prop_adder.v`) by chaining four `full_adder` instances in **Vivado’s IP Integrator** ().  
  - Simulated `prop_adder.v` to confirm correct 4-bit addition and carry-propagation behavior.  
- **Reading**  
  - Read about full-adder and ripple-carry adder architectures .  
  - Read about cascading full-adders for multi-bit addition.

#### 📅 Friday, May 23
- **Synthesis & Resource Analysis**  
  - Ran synthesis in Vivado for `half_adder.v`, `full_adder.v`, and `prop_adder.v`.  
  - Examined **Utilization Report**:  
    - Half Adder → 1 LUT, 0 FFs  
    - Full Adder → 2 LUTs + 1 LUT for OR, 3 FFs  
    - 4-bit CPA → 4 × (full adder) LUT usage + routing overhead ().  
  - Viewed **CLB Mapping**: traced how LUT outputs feed into adjacent CLBs to propagate carry.  
- **Weekly Documentation**  
  - Wrote three short blog posts:  
    1. **SRAM Basics:** detailed 6-T cell operation and how LUT/SRAM bits store truth tables.  
    2. **Bistable Flip-Flops:** explained edge-triggered D-FF operation, asynchronous reset, and how FPGA fabric implements them.  
    3. **LUT Internals:** described how LUTs map their address bits into SRAM contents to realize arbitrary Boolean functions.  

---

### 3. Key Learnings
- **Configurable Logic Block (CLB)**  
  - A CLB contains several small LUTs, flip-flops, and local multiplexers. The LUT is implemented using SRAM cells to encode up to a 4- or 6-input Boolean function.
- **Look-Up Tables (LUTs)**  
  - Each LUT uses SRAM bits to store a truth-table; any combination of inputs addresses that table. Post-synthesis, I observed per-LUT utilization metrics.  
- **Block RAM (SRAM)**  
  - Larger on-chip memory blocks consist of arrays of SRAM cells. They are inferred in Verilog via `ram_style = “block”` or instantiated via IP; useful for data storage in larger designs.  
- **Vivado Flow**  
  - Typical flow:  
    1. **Project setup** 
    2. **HDL source & test-bench creation**  
    3. **Simulation** (XSim behavioral)  
    4. **Synthesis** → **Implementation** (place & route)  
    5. **Bitstream generation** → **Programming**  
  - Setting up the correct `.xdc` constraint file is crucial before implementation.  
- **Arithmetic Modules**  
  - **Half Adder:** implemented as `sum = a ^ b`, `carry = a & b`.  
  - **Full Adder:** two half-adders cascaded + `cout = c1 | c2`.  
  - **4-bit CPA:** cascades four full adders; carry-out of stage _i_ feeds carry-in of stage _i + 1_.  
  - Resource scaling: 4-bit CPA uses ~4× LUT resources of a single full adder plus interconnect.

---

### 4. Additional Activities
- **Obsidian → Hugo Integration**  
  - Initialize an Obsidian vault for note-taking and blog drafts.  
  - Configure a Hugo site locally (install Hugo, choose a theme).  
  - Link Obsidian’s Markdown folder to Hugo’s `content/` directory so notes automatically become Hugo blog posts.
- **Deployment on Vercel**  
  - Set up a GitHub repository containing the Hugo site.  
  - Connect the repo to Vercel for automatic deployments on commits to `main`.  
  - Verify that pushing a new Markdown file (via Obsidian sync) triggers Hugo rebuild and Vercel deployment.

---
