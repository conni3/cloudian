---
title: DSP slices
draft: true
---
dedicated hardware blocks optimized for arithmetic-intensive operations—most notably multiplication and accumulation
higher performance and lower power for signal-processing algorithms such as filters, transforms, and dot-products


dot products are signal-processing algorithm?


Beyond simple MAC, a single DSP slice can be configured to perform:

- Multiply-only or add-only operations
    
- Multiply-add (MADD) and three-input addition
    
- Barrel shifting and wide-bus multiplexing
    
- Magnitude comparison and pattern detection
    
- Synchronous up/down counting (using the accumulator as a counter)
    
- Custom bitwise logic functions
    
- SIMD arithmetic (dual or quad lanes)  
    All these modes are selected via control signals (OPMODE) at runtime