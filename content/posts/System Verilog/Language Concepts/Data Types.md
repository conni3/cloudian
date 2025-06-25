---
title: Data Types
draft: true
---

#### 1. [**Net Types (4-state, driven by continuous assignments)**](/posts/system-verilog/nets/)

- `wire`
	
- `tri`, `tri0`, `tri1`, `triand`, `trior`, `wand`, `wor`
	
- `uwire` (unresolved wire)
	
- `supply0`, `supply1`
	
- Differences: driven vs unresolved, contention resolution rules

#### 2. **Variable Types (Procedural, Can Hold state)**

- [`logic`](/posts/system-verilog/logic-data-type/) (4-state)
	
- `reg` (legacy, same as `logic`)
	
- `bit` (2-state)
	
- `byte`, `shortint`, `int`, `longint`
	
- `integer`, `time` (legacy types)

#### 3. **Vector Types**

- Packed arrays (bit-vectors): `logic [31:0]`, `bit signed [15:0]`
	
- Unpacked arrays: `int array_name[10]`
	
- Packed vs Unpacked: layout and use in synthesis

#### 4. **User-defined Types**

- `typedef` (aliased types)
	
- `enum` (enumerated states, FSM coding)
	
- `struct` (grouping related signals)
	
- `union` (memory-efficient overlapping fields)

#### 5. **Composite & Interface Types**

- `interface` (e.g. `tilelink_if`, `axi4lite_if`)
	
- `modport` (port direction specification in interfaces)
	
- Interface instantiation and usage patterns

#### 6. **Dynamic & Queue Types**

- Dynamic arrays: `int dyn_array[]`
	
- Queues: `int queue[$]`
	
- Associative arrays: `int aa[string]`

#### 7. **Classes & Object-Oriented Types** (mostly Testbench and UVM)

- `class`, `virtual`, `extends`
	
- Object handles, inheritance, polymorphism
	
- Constructor & method usage

#### 8. **Special Types & Keywords**

- `void`, `null`, `event`
	
- `chandle` (C pointers)
	
- DPI types (`import "DPI-C"`)

#### 9. **Const, Parameter & Macro-defined Types**

- `parameter`, `localparam`
	
- `const`, `static`, `automatic`
	
- `define` macros in `macros_pkg.sv`

#### 10. **Coverage & Assertion Data Types**

- `covergroup`, `coverpoint`
	
- `sequence`, `property`, `assert`
	
- Clocking blocks and sampled values
