---
title: "Debugging a Half-Adder Testbench: A Journey in Four Lessons"
draft: false
---

When I set out expecting a quick smoke test for my pure combinational half-adder in SystemVerilog, I expected it to be trivial. Instead, I learned more about assertions, build scripts, and wildcard patterns than I ever thought I would. What began as a syntax error turned into a four-step masterclass in testbench design.

## Lesson 1: The SVA “Watch” Myth

I was sure I could “watch” my 2-bit input vector directly:

```systemverilog
@(ab_combined) …
```

But SystemVerilog properties demand explicit edges (`posedge` or `negedge`). The parser’s complaint—“expecting edge or negedge or posedge”—taught me that there’s no built‑in change‑detector syntax in SVA. You either:

- Drive checks on a clock edge, or
	
- Use immediate assertions in an `always_comb` block

## Lesson 2: Combinational Tests vs. Clocked Assertions

My half-adder doesn’t need a clock—but SVA properties do. I discovered two clean patterns:

1. **Immediate assertions**
	
	```systemverilog
    always_comb begin
      assert(sum === a^b)   else $error("…");
      assert(carry === a&b) else $error("…");
    end
    ```

	No clock required; checks fire as soon as inputs or outputs change.

2. **Dedicated TB clock**  
	Declare
	
	```systemverilog
    input logic clk;
    ```

	in the module header and drive it from the C++ harness. That clock only paces the assertions—your DUT remains purely combinational.

Along the way I learned that declaring `logic clk;` inside the module body doesn’t expose it to Verilator’s C++ driver—only ports become public members.

## Lesson 3: Makefile Wildcard Woes

My Makefile used this pattern:

```makefile
modules/*/tb/half_adder_tb.sv
```

…but my testbench lived at:

```
modules/arithmetic/half_adder/tb/half_adder_tb.sv
```

A missing `*` cost me countless rebuilds. Changing to:

```makefile
modules/*/*/tb/half_adder_tb.sv
```

instantly fixed Verilator’s “Cannot find file containing module” error.

## Lesson 4: Sequential vs. Combinational Dispatch

The build script classifies any TB containing the string `posedge clk` as **sequential**, pulling in `sim_main.cpp` that tries to toggle a `clk` port. Without that port, compilation fails. Removing the stray `posedge clk` (or properly making `clk` a port) let the **combinational** rule run with `sim_main_minimal.cpp`, and suddenly everything passed.

---

**Takeaway:**

- **SVA assertions** aren’t magical “watches”—they need edges or immediate checks.
	
- **Combinational DUTs** can use either `always_comb` asserts or a separate TB clock.
	
- **Wildcard patterns** in Makefiles must match directory depth exactly.
	
- **Build rules** can hinge on simple text matches, so stray keywords change behavior.

With these insights, my half-adder now simulates cleanly every time.