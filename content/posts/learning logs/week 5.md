---
title: Week 5
date: 2025-06-20
tags:
  - calas
  - learning_log
---
## Week 5 Learning Log (June 16–20, 2025)

### 1. Objectives

- **Library Documentation**
    
    - Finalize docs 01–07 for RVSvKit
        
- **Repository & CI Scaffolding**
    
    - Set up the RVSvKit GitHub repo
        
    - Add scaffolding scripts for build/test automation
        
- **Dependency Installation**
    
    - Verilator, Icarus, Dockerized Vivado
        
- **SystemVerilog Fundamentals**
    
    - Ports
        
    - Nets vs. variables
        
    - Tasks vs. functions
        

---

### 2. Daily Activities

#### 📅 Monday, June 16

- **Docs 01 & 02**
    
    - Completed writing the **Overview** and **Module Inventory** documents.
        
- **Installed Verilator**
    
    - Installed via package manager; ran `verilator --version` to confirm toolchain.
        
- **SV Fundamentals – Ports**
    
    - Reviewed `input`/`output`/`inout` declarations, named vs. ordered port lists, and port-type semantics.
        

#### 📅 Tuesday, June 17

- **Docs 03 & 04**
    
    - Drafted **Coding Conventions** and **Packages & Interfaces** sections.
        
- **Installed Icarus**
    
    - Installed `iverilog`; verified v11.0.0 via `iverilog --version`.
        
- **SV Fundamentals – Nets vs. Variables**
    
    - Studied `wire` vs. `logic/reg`, implicit nets, driver resolution and multiple-driver rules.
        

#### 📅 Wednesday, June 18

- **Docs 05 & 06**
    
    - Wrote **CI & Testing** and **Automation & Optimization** chapters.
        
- **Dockerized Vivado Setup**
    
    - Created Dockerfile for Vivado 2024.2; built container and ran a simple synthesis smoke test.
        
- **SV Fundamentals – Tasks vs. Functions**
    
    - Compared syntax, side-effects, timing control; wrote examples to illustrate use cases.
        

#### 📅 Thursday, June 19

- **Doc 07**
    
    - Finalized **Contributing & Versioning**, outlined future cache/MMU work and internship context.
        
- **Initialize RVSvKit Repo**
    
    - Created GitHub repo, pushed initial commit with all docs.
        
- **Add Scaffolding Scripts**
    
    - Added `Makefile`, GitHub Actions workflow for lint, simulation, and documentation checks.
        

#### 📅 Friday, June 20

- **Review & Proof**
    
    - Polished all seven docs for style consistency; updated cross-references.
        
- **Integrate Dependencies into CI**
    
    - Extended Actions workflow to install Verilator, Icarus, and Docker Vivado before tests.
        
- **Consolidated SV Notes**
    
    - Compiled a cheat-sheet covering ports, nets/variables, tasks/functions for quick reference.
        

---

### 3. Key Learnings

- **Modular Documentation Workflow**  
    Dividing the seven docs across days ensured steady progress and consistent style.
    
- **Early CI Integration**  
    Scaffolding scripts and tool installs in CI guarantee reproducible builds and tests.
    
- **Containerized FPGA Toolchain**  
    Dockerizing Vivado simplifies environment setup for all team members.
    
- **SV Fundamentals Mastery**  
    Deepened understanding of port semantics, net/variable distinctions, and procedural constructs.