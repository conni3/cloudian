---
draft: true
---
MIPS (Microprocessor without Interlocked Pipeline Stages) 

- a classic RISC (Reduced Instruction Set Computer) architecture
- simplicity, efficiency, and ease of pipelining. 
- clean, regular instruction formats
- five-stage pipeline


found in embedded devices where intruction set is nearly invisible, so it is hard to find a computer to download and run mips programs

core principles:
- risc
	- fixed length instructions
	- simple load/store model ???
	- large register file
- orthogonality
	- uniform inst formats
	- consistent use of register operands ????
- pipelining friendly
	- minimal data dependencies -> no complex addressing modes
	- interlocks handled in hardware so isa is clean


instruction formats:
r type -> opcode (6) rs (5)
i type  -> opcode (6) rs (5)
j type  -> opcode (6) address (26)

5 stage pipeline
one instruction per cycle

IF (instruction fetch)
- read next inst from inst memory (PC)

ID (instruction decode)
- decode opcode 
- read regs rs and rt
- sign-extend immediate ???

EX (execute)
- alu ops
- calc branch target

MEM (memory access)
- - load from or store to memory

WB (write back)
- write alu or mem results back to register file

key components
- pc
- inst mem
- reg (32 x 32 bits)
- alu w/ control signals
- data mem
- sign-extension and mux (selecting inputs)

control unit
- main control
	- decodes 6 bit opcode to generate signals:
		- RegDst, ALUSrc, MemToReg, RegWrite, MemRead, MemWrite, Branch, Jump
- alu control
	- further decode funct (r type) + 2 bit ALUOp
	- choose exact ALU operation

Handling hazards
1. Data hazards: when an inst depends on a prior inst result
	1. forwarding (bypassing)
		1. route alu outputs directly to the inputs of a following instruction
	2. pipeline stalls (interlocks)
		1. hardware inserts "bubbles" until data is ready
2. Control hazards: from branches and jumps
	1. delayed branch
		1. instruction immediately after a branch is always executed
	2. Branch prediction
		1. more advanced mips implementations
3. structural hazards: resource conflicts
	1. mips avoids this by having separate inst and data memories (harvard style) and separate alu and registers ports