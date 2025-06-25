---
title: "Data Type: Nets"
tags:
  - calas
  - system_verilog
  - theory
draft: false
---

Nets model physical connections between drivers. When you have multiple drivers

All net types are inherently **four-state** - each bit can be 0, 1, X (unknown) or Z (high-impedance). This is due to several reasons.

---

Nets have to have more than 2 states (binary values) because they allow multiple drivers. They must allow X and Z states to model un-driven or partially-driven connections. When there are multiple sources (like bus signals or tri-state buffers), there might be a conflict. When there is a conflict the net will have X value and Z if there is no drivers.

---
### Floating (Z)

The `z` state specifically refers to **a floating or un-driven condition**—the net is not being actively driven by any source.

When there are multiple drivers:

- If one driver puts `z` and another puts `1`, the result is `1`.
- If one driver puts `z` and another puts `z`, the result is `z`.
- If one driver puts `1`, another puts `0`, result is `x` (conflict).

---

### Contention (X)

Since multiple drivers can "pushes" a value to the same port, there would be some conflict. In that case, simulation resolves it to X to flag the conflict.

```verilog
module A(output wire a); assign a = 1; endmodule
module B(output wire b); assign b = 0; endmodule

wire foo;
A u1(.a(foo));
B u2(.b(foo));

// foo sees 1 from A and 0 from B → foo becomes X (conflict)
```

---
#### Contention Resolution

Whenever there is a conflict, simulation uses a table shown below to resolve the conflict:

|Driver A \ Driver B|0|1|X|Z|
|---|---|---|---|---|
|**0**|0|**X**|**X**|0|
|**1**|**X**|1|**X**|1|
|**X**|**X**|**X**|**X**|**X**|

---
## Net Types

1. **Basic Nets**
Wires require one driver or resolves them using wired logic. It simply represents a physical connection.
- `wire` (4-state): the most common net
- `wire [N-1:0] bus` is simply an N-bit vector of wires.
	It is N individual 1-bit nets all bundled under one name. It tells the compiler “I want N separate wires, numbered 0 through N-1".
	**On an FPGA or ASIC**, each bit of that vector becomes its own metal interconnect (or FPGA routing wire). When you hook a 32-bit bus between two modules, the placer & router will physically lay out 32 parallel tracks.

---

1. **Pulled Nets:**
It is an alias for wire, but used when we expect there to be multiple drivers. It has pull up, which means a default state when there are no drivers.
- `tri0/tri1`: when undriven, defaults to 0 or 1.
- `trireg`: - like `wire`, but with an implicit pull-down resistor.

---

1. **Wired-AND / Wired-OR**
They are resolved net types. Instead of returning `x` on multiple conflicting drivers, **`wand` and `wor` resolve the multiple drivers using logic rules**:
- `wand`: **Open-drain**: any driver pulling low causes low output. All must be high (or unconnected) for output to be high.
- `wor`: **Open-source**: any driver pulling high causes high output. All must be low (or unconnected) for output to be low.

---

1. **Supply Nets**
- `supply1` models a net tied directly to **Vcc (logic high)**.
- `supply0` models a net tied directly to **GND (logic low)**.

---
## Summary Table

|Net Type|Value Type|4-State?|Multi-Driver?|Default Value|Resolves?|Strength|Typical Use Case|
|---|---|---|---|---|---|---|---|
|`wire`|4-state|✅|Yes|`'z` (unconnected)|❌ (x on conflict)|Medium (strong)|General-purpose signal connection|
|`tri`|4-state|✅|Yes|`'z`|❌ (x on conflict)|Medium (strong)|Tri-state buses, shared data lines|
|`tri0`|4-state|✅|Yes|`0` when undriven|❌|Weak pull-down|Open-collector lines, bus defaults to 0|
|`tri1`|4-state|✅|Yes|`1` when undriven|❌|Weak pull-up|Open-drain lines, bus defaults to 1|
|`wand`|4-state|✅|Yes|`'z`|✅ (AND)|Resolved|Wired-AND logic, bus arbitration|
|`wor`|4-state|✅|Yes|`'z`|✅ (OR)|Resolved|Wired-OR logic, interrupt aggregation|
|`uwire`|2-state|❌|No|`0`|❌|Strong|Untyped wire; more efficient (for synthesis only)|
|`supply0`|constant|❌|N/A|`0`|Constant|Strongest|Connect to GND, power modeling|
|`supply1`|constant|❌|N/A|`1`|Constant|Strongest|Connect to Vcc, power modeling|
|`wand0`|4-state|✅|Yes|`0`|✅ (AND)|Resolved|(Rarely used) wired-AND with default 0|
|`wor1`|4-state|✅|Yes|`1`|✅ (OR)|Resolved|(Rarely used) wired-OR with default 1|

---