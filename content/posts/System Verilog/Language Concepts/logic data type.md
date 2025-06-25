---
title: "Data Type: Logic"
---

SystemVerilog introduces `logic` as a **4-state** data type that **can be assigned in `initial`, `always`, or `always_comb` blocks**. Unlike `wire`, which is only for continuous assignments (i.e., driven by `assign` or module ports), `logic` supports **procedural assignments**.

```
logic a;
initial begin
  a = 1'b0; // legal because a is logic
end
```

But if we use wire, then it is illegal.

```
wire a;
initial begin
  a = 1'b0; // illegal: can't assign to wire from procedural block
end
```

In a real design, `wire` is for nets connected to actual gates/drivers and `tri` is for tristate buses. But in testbenches, you often **drive values directly from `initial` or `always` blocks**, so you want **something that can hold a value without requiring a driver** → that’s `logic`
