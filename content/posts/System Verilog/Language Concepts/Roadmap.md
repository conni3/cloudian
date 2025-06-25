---
title: Roadmap
draft: true
---
- **Language Basics**  
	1.1. Lexical conventions: identifiers, comments (`//`, `/*…*/`), white space  
	1.2. Preprocessor: `` `define ``, `` `include ``, conditionals (`ifdef`, `ifndef`)  
	1.3. File organization & naming
	
- **Data Types & Declarations**  
	2.1. Nets vs. variables: `wire`, `logic` (4-state) vs. `bit` (2-state)  
	2.2. Integer types: `byte`, `shortint`, `int`, `longint`, `integer`  
	2.3. Real types: `real`, `realtime`  
	2.4. Enumerations (`enum`), `typedef`  
	2.5. Composite types: `struct`, `union`  
	2.6. Arrays: packed vs. unpacked, dynamic arrays, queues, associative arrays  
	2.7. Strings
	
- **Operators**  
	3.1. Arithmetic, relational, logical  
	3.2. Bitwise, reduction (`&`, `|`, `^`, `~&`, etc.)  
	3.3. Streaming (`{<< , >>}`) and assignment patterns  
	3.4. Inside, wildcard (`?`), concatenation
	
- **Modules & Hierarchy**  
	4.1. `module` declaration: ports, parameters, parameters vs. localparams  
	4.2. Port lists: ordered vs. named connections  
	4.3. Parameterization: default parameters, `parameter int WIDTH = …`  
	4.4. Generate constructs: `generate`/`endgenerate`, `for`–`genvar` loops
	
- **Interfaces & Packages**  
	5.1. `package` basics: sharing `typedef`, parameters, macros  
	5.2. `interface` blocks: bundling signals, modports  
	5.3. Clocking blocks inside interfaces  
	5.4. Virtual interfaces for testbench–DUT connection
	
- **Procedural Constructs**  
	6.1. Always blocks:  
	  – `always_comb` for combinational logic  
	  – `always_ff @ (posedge clk…)` for sequential  
	  – `always_latch` when needed  
	6.2. `initial` and `final` blocks  
	6.3. Control flow: `if`/`else`, `case` (`unique`/`priority`), loops (`for`, `while`, `foreach`)
	
- **Tasks & Functions**  
	7.1. `function`: no timing control, must return a value  
	7.2. `task`: can include delays, no return value  
	7.3. System tasks/functions: `$display`, `$finish`, `$random`, etc.
	
- **Concurrency & Timing Control**  
	8.1. Continuous assignments (`assign`)  
	8.2. Event controls: `@ (posedge clk)`, `@*`, event triggers  
	8.3. Fork–join for parallel processes
	
- **Assertions & Coverage**  
	9.1. Immediate assertions: `assert (…);` inside procedural code  
	9.2. Concurrent assertions: `property`, `sequence`, `assert property`  
	9.3. Coverage: `covergroup`, `coverpoint`, cross coverage
	
- **Object-Oriented & Randomization**  
	10.1. Classes: `class` definition, constructors, methods  
	10.2. Inheritance and virtual methods  
	10.3. Randomization: `rand`/`randc`, `constraint` blocks, `post_randomize`  
	10.4. Factory patterns (foundation for UVM)
	
- **DPI & External Interfacing**  
	11.1. DPI import/export (`import "DPI-C"` / `export "DPI-C"`)  
	11.2. Interfacing C/C++ routines for modeling or co-simulation
	
- **Synthesis vs. Verification**  
	12.1. Synthesizable subset: modules, `always_ff`, `always_comb`, `generate`, parameterization  
	12.2. Non-synthesizable features: classes, dynamic arrays, randomization, pure simulation constructs  
	12.3. Synthesis directives/pragmas (`/* synthesis … */`)
	
- **Practical Testbench Organization**  
	13.1. Testbench structure: DUT instantiation, stimulus drivers, monitors  
	13.2. Use of `program` blocks  
	13.3. Clock and reset generators (clocking blocks)  
	13.4. Integration with simulators & CI (Verilator, Icarus, Vivado)
	
- **Coding Style & Conventions**  
	14.1. Indentation, naming (snake_case vs. UPPER_SNAKE_CASE)  
	14.2. File and module naming (`half_adder.sv` ⇒ `module half_adder`)  
	14.3. Blocking vs. non-blocking assignments guidelines  
	14.4. Header comments and documentation stubs