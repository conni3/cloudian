---
title: 555 Timers
draft: true
tags:
  - calas
  - digital_logic
  - theory
---
## Definition

555 timers is the most beloved and used integrated circuits, used mainly for timing and waveform generation. It is used in blinking LEDs, PWM, and oscillator circuits. 

## Modes

It is defined as a "**highly stable multivibrator circuit**" - which means it is basically a circuit that can flip between 2 or more voltage stages in a controlled way. It has 3 modes:

1. Monostable

In this mode, the circuit/timer acts like a stopwatch where you press and button and it gives you one timed pulse

2. Astable

In this mode, 555 timer is like a blinking light - flipping on and off continuously.

3. Bistable

The last mode is like a light switch. To toggle on or off, you have to do it manually.

## Anatomy:

![](/images/555.webp)[Anatomy of a 555 timer from Circuit Basics]

**Voltage divider**: 
From the image you can see there are three 5k$\ohm$ resistors, hence the name 5-5-5. These resistors divide the power supply to 2/3 VCC and 1/3 VCC.

**Two Comparators:**
They compare the voltages (Threshold voltage at pin 6 and Trigger Voltage at pin 2) and set/reset the output.

**SR Flip-Flop**:
Memory element that controls the output state. The outputs from the comparator feeds into S and R inputs of the flip-flop. 

**Discharge capacitor:**
When values change from 1 to 0, the capacitor discharges the value.

**Amplifier**:
The output of the SR flip flop also connect with an amplifier before going to the output pin.

