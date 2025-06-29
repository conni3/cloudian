---
title: SRAM
tags:
  - calas
  - theory
  - digital_logic
showTableOfContents: true
showHeadingAnchors: true
draft: false
---

SRAMs are static memory. They are implemented using 6 transistors usually and because of that more expensive. 

Fills 2 needs:

1. direct interface with CPU at speeds not attainable by [DRAM](/posts/contentcalastheoriesdram/)s
2. replace DRAMs in systems with very low power consumption

In 1st use, SRAM serves as cache memory, interfacing between DRAMs and the CPU

![](/images/Pasted%20image%2020250524194226.png)

For 2nd use, SRAM is used instead of DRAM. This is because DRAM refresh current is several orders of magnitude more than the low-power SRAM standby current. 

Access time is comparable to DRAMs in low power mode.

### How it Works

![](/images/Pasted%20image%2020250524221931.png)

Consists of [bi-stable flip flop](/posts/bistable-flip-flop/)s connected to the internal circuity by two access transistors. 

It has 3 states:

- Idle State
	- When not addressed, the access transistors are off and flip flops maintain their state, preserving the stored data.
- Read Operation
	- Activating the world line turns on the access transistors, connecting the flip flops to bit lines. Sense amplifiers detect the logic level and transfer it to the output.
- Write operation
	- Data from the input is driven onto the bit lines, overriding the existing state due to stronger write drivers.

Compared to [DRAM](/posts/contentcalastheoriesdram/), SRAM only needs power supply for stable data.

### Types
- 4T Cell
	- Four NMOS transistors with two poly load resistors
- 6T Cell
	- Four NMOS and two PMOS transistors, (better stability and performance)
- TFT Cell
	- Utilizes thin-film transistors (often used in applications like display technologies)

### Applications:

- **Cache memory**: L1 and L2 caches in CPUs
- **Storage buffers**: Temporary storage in storage devices
- **Industrial and Peripheral buffers**: Networking equipment and other peripherals

___

References:

https://web.eecs.umich.edu/~prabal/teaching/eecs373-f11/readings/sram-technology.pdf
