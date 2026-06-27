# FPGA-Based CORDIC Exponential Function Accelerator

Custom instruction extension for the **Microwatt** OpenPOWER soft-core processor
implementing eˣ via CORDIC hyperbolic mode on Xilinx Arty A7-100T FPGA board.

## Overview
- Uses Xilinx CORDIC v6.0 IP in Sinh and Cosh mode
- Identity used: eˣ = sinh(x) + cosh(x)
- Integrated as a custom ISA instruction (OP_EXP) in the Microwatt pipeline
- Q1.15 fixed-point input format, 32-bit output per channel

## Key Results

| Method        | Total Power (W) | WNS (ns) | DSP Slices |
|---------------|-----------------|----------|------------|
| CORDIC        | 0.30            | 2.804    | 36         |
| Taylor Series | 0.685           | 0.323    | 88         |
| C Math Lib    | 0.824           | 0.358    | 36         |

CORDIC achieves 63% lower power than the C Math implementation
with the best timing margin.

## Tools Used
- Xilinx Vivado 2019.2
- Target Board: Xilinx Arty A7-100T (xc7a100tcsg324-1)
- Hardware Description Language: VHDL
- Processor: Microwatt OpenPOWER soft-core

## Project Paper
The full research paper is available in the `docs/` folder.
