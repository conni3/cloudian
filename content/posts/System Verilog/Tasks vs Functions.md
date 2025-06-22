---
title: Tasks vs Functions
showTableOfContents:
---
Both functions and tasks are subroutines that are reusable RTL or testbench codes.

## Return value and Argument directions
### Function

- must return a single value, whose function you declare in the header
- arguments are all inputs, cannot declare output or inout ports
- called from expressions ` y = my_func(a,b);`

### Task

- does not return value directly, to get data out, must use output or inout arguments
- can have input, output, and inout ports
- called as a standalone statement `my_task(a,b,c,)`, not inside an expression

## Timing control and simulation time

### Function

- cannot include any timing controls (`@, wait, #delay`) or non-zero simulation-time constructs
- must execute in zero simulation time - pure combinational logic

### Task

- can include timing controls, delays, event controls, and even `fork ... join`
- useful for driving testbenches or modeling multi-cycle behaviors.

## Usage in RTL vs. testbench

- **Functions** are used in small, combinational operations such as checksum, bit-field packing, and arithmetic helpers.
- **Tasks** are used when you need a sequence of events such as stimulus generation, bus transactions, and waiting for handshakes

## Calling rules and synthesis
### Functions 

- can be called anywhere an expression is allowed (assign statements, inside procedural blocks, and in parameter calculations)
- synthesizable if they are zero-time and returns single value.

### Tasks

- cannot be used in expressions
- generally not synthesizable and used most often in testbenches

## Example
### Function

```sv
function int add (input a, input int b);
	add = a + b;
endfunction
```

### Task

```sv
task wait_for_flag(
	input logic clk,
	input logic flag,
	output int count);
	
	count = 0;
	while (!flag) begin
		@(posedge clk);
		count++;
	end
	
endtask
```