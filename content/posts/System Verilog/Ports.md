---
title: Ports
draft: true
---
Every module or interface exposes a list of ports - points of connection where signal, handshakes or buses flow in and out. They are declared either in **Headers** or **Port-declaration blocks**.

## Directions

| Direction | Role                   | Usage                                       | More                                                                                                                                         |
| --------- | ---------------------- | ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `input`   | Consumed by the module | Clock, resets, data inputs, control signals | Read-only inside modules                                                                                                                     |
| `output`  | Driven by the module   | Results, flags and response signals         | Produces a value, by default is a net (wire), but when they are variable (e.g.`logic`) type, they behave like registers in procedural blocks |
| `inout`   | Bi-directional         | Shared buses, tri-state pins, wires on I/O  | Live on a net and allows both the module and the environment to drive value and are typically gated by enable signals                        |

## Net vs. Variable Ports


## Interfaces as Ports

Rather than having  


## Parameterization

## Overriding Parameters
## Port-Connection Styles
## Reading & Passing Parameters at Runtime
