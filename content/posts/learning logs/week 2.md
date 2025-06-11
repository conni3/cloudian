---
title: Week 2
draft: false
date: 2025-05-39
showHeadingAnchors: true
showTableOfContents: true
tags:
  - calas
  - learning_log
---
## Week 2 Learning Log (May 26–30, 2025)

### 1. Objectives
- **HDL Implementation & Simulation**  
  - Implement and simulate the following combinational primitives:  
    - 4-bit Subtractor (`subtractor4.v`)  
    - 2-to-1 Multiplexer (`mux2to1.v`)  
    - 4-to-1 Multiplexer (`mux4to1.v`)  
- **Toolflow Practice**  
  - Create testbenches to verify each module in XSim  
  - Synthesize all Week 2 designs in Vivado and analyze LUT/CLB usage  
- **Documentation & Blogging**  
  - Draft blog posts on subtractor design (two’s-complement) and multiplexer architectures  
- **Reading (acquired Friday, May 30)**  
  - Start reading Harris & Harris and Patterson & Hennessy chapters on combinational components

---

### 2. Daily Activities

#### 📅 Monday, May 26
- **4-bit Subtractor (`subtractor4.v`)**  
  - Designed two’s-complement subtractor by inverting B inputs, adding 1 (carry-in) to a 4-bit adder.  
  - Wrote `subtractor4.v`:  
    ```verilog
    module subtractor4 (
      input  [3:0] A,
      input  [3:0] B,
      output [3:0] D,
      output       BorrowOut
    );
      wire [3:0] B_inv;
      wire       carry_in = 1'b1;
      assign B_inv = ~B;  // bitwise invert B
      // reuse prop_adder for A + (¬B) + 1
      prop_adder adder_inst (
        .A    (A),
        .B    (B_inv),
        .CI   (carry_in),
        .SUM  (D),
        .CO   (BorrowOut)
      );
    endmodule
    ```
  - Created testbench `subtractor4_tb.v` applying A,B pairs:  
    - (4’b0101 – 4’b0011 = 2)  
    - (4’b0010 – 4’b0100 = –2)  
    - (4’b1000 – 4’b1000 = 0), etc.  
  - Simulated in XSim; confirmed correct 4-bit difference and borrow flag.

#### 📅 Tuesday, May 27
- **2-to-1 Multiplexer (`mux2to1.v`)**  
  - Wrote `mux2to1.v` to select between two 8-bit inputs for practice:  
    ```verilog
    module mux2to1 #(
      parameter WIDTH = 8
    )(
      input  [WIDTH-1:0] D0,
      input  [WIDTH-1:0] D1,
      input              SEL,
      output [WIDTH-1:0] Y
    );
      assign Y = SEL ? D1 : D0;
    endmodule
    ```
  - Created `mux2to1_tb.v` to test all SEL / data combinations (e.g., D0=8’hAA, D1=8’h55).  
  - Ran XSim behavioral simulation; verified correct output switching.

#### 📅 Wednesday, May 28
- **Meeting with Sanka & Verilog Syntax Review**  
  - Met with Sanka to go over Verilog syntax nuances: module definitions, `always` blocks, non-blocking vs. blocking assignments, and best practices for naming conventions.
- **4-to-1 Multiplexer (`mux4to1.v`)**  
  - Extended multiplexer logic to four inputs:  
    ```verilog
    module mux4to1 #(
      parameter WIDTH = 8
    )(
      input  [WIDTH-1:0] D0,
      input  [WIDTH-1:0] D1,
      input  [WIDTH-1:0] D2,
      input  [WIDTH-1:0] D3,
      input  [1:0]       SEL,
      output [WIDTH-1:0] Y
    );
      always @(*) begin
        case (SEL)
          2'b00: Y = D0;
          2'b01: Y = D1;
          2'b10: Y = D2;
          2'b11: Y = D3;
        endcase
      end
    endmodule
    ```
  - Wrote `mux4to1_tb.v` to exercise SEL = 00,01,10,11 with distinct patterns on D0–D3.  
  - Simulated to confirm correct selection and no glitches.

#### 📅 Thursday, May 29
- **Synthesis & Resource Analysis**  
  - Added `subtractor4.v`, `mux2to1.v`, and `mux4to1.v` to a Vivado project.  
  - Ran synthesis for each module:  
    - **Subtractor4** → used ~5 LUTs (4 for each inverted bit & one for adder instrumentation).  
    - **Mux2to1 (8-bit)** → 8 LUTs (one per bit).  
    - **Mux4to1 (8-bit)** → ~16 LUTs (2:1 trees or equivalent).  
  - Reviewed **Utilization Reports** and **CLB Mapping** to understand LUT distribution and routing overhead.  
- **Blog Writing**  
  - Drafted a post: **“Implementing a 4-bit Two’s-Complement Subtractor”** covering:  
    1. Two’s-complement basics (invert + add 1).  
    2. Verilog implementation leveraging the existing `prop_adder`.  
    3. Simulation results and borrow-out interpretation.  
  - Drafted a post: **“Multiplexer Architectures in FPGA”** covering:  
    1. 2:1 vs. 4:1 multiplexer logic.  
    2. LUT-based implementation and resource considerations.  
    3. Simulation snapshots illustrating glitch-free switching.

#### 📅 Friday, May 30
- **Book Access & Reading**  
  - Received **Digital Design & Computer Architecture (Harris & Harris)** and **Computer Organization & Design (Patterson & Hennessy)**.  
  - Read **Harris & Harris, Ch 2 (Sect 2.4 “Adders and Subtractors”)** to reinforce subtractor theory and comparator design.  
  - Read **Harris & Harris, Ch 3 (Sect 3.2 “Multiplexers and Demultiplexers”)** for mux implementation details.  
  - Read **Patterson & Hennessy, Ch 3 (Sect 3.3 “Subtracters and Extensions”)** and **Ch 2 (Sect 2.2 “R-Type ALU Operations”)** for context on how subtractors map to ALU control signals.  
  - Made notes on best practices for coding subtractors/multiplexers in Verilog and FPGA-friendly optimizations.

---

### 3. Key Learnings
- **Two’s-Complement Subtraction**  
  - Implemented as A + (~B) + 1; borrow-out corresponds to final carry-out.  
  - Reusing a ripple-carry adder greatly simplifies subtractor design.
- **Multiplexer Implementation**  
  - *2-to-1 Mux*: single LUT per bit when width = 1; for WIDTH > 1, replicate per bit.  
  - *4-to-1 Mux*: often built as two cascaded 2:1 stages → higher LUT count; careful case coding avoids glitches.
- **Verilog Syntax Refinement**  
  - Distinction between blocking (`=`) and non-blocking (`<=`) assignments in sequential logic.  
  - Best practices: use clear module port lists, consistent indentation, and meaningful signal names.  
  - Importance of `always @(*)` for purely combinational `case` statements.

- **Resource Utilization**  
  - *Subtractor4* consumed ~5 LUTs + routing.  
  - *Mux2to1 (8-bit)* used 8 LUTs; *Mux4to1 (8-bit)* used ~16 LUTs.  
  - Vivado’s utilization reports help anticipate resource requirements for larger datapaths.

- **Reading Insights**  
  - *Harris & Harris Ch 2–3* emphasize building subtractors via inverter + adder and show LUT-based mux implementations.  
  - *Patterson & Hennessy* clarify how ALU control signals select between operations (ADD vs. SUB, etc.), reinforcing Week 3 FSM control concepts.

---
