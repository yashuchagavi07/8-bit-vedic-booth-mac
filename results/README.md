# Design and Performance Analysis of 16-Bit Vedic and Booth Multipliers Using MAC Unit

## Overview

This project presents the design and comparative performance analysis of two multiplier architectures integrated into a common Multiply-Accumulate (MAC) architecture:

* **16-bit Vedic Multiplier** based on the Urdhva-Tiryakbhyam algorithm
* **16-bit Radix-4 Booth Multiplier**

Both multiplier architectures are integrated with the same accumulation structure to enable a fair comparison of their hardware and performance characteristics.

The designs are described using **Verilog HDL**, functionally verified using **Cadence SimVision**, and synthesized using **Cadence Genus** with the **TSMC 180 nm technology library**.

## MAC Architecture

The MAC performs the operation:

```text
MAC = (A × B) + Accumulator
```

The architecture consists of three primary blocks:

```text
16-bit Multiplicand ──┐
                     │
16-bit Multiplier ───┤
                     ▼
              ┌─────────────┐
              │  Multiplier │
              └──────┬──────┘
                     │
                 32-bit
                  Product
                     │
                     ▼
              ┌─────────────┐
              │    Adder    │
              └──────┬──────┘
                     │
                     ▼
              ┌─────────────┐
              │ Accumulator │
              └──────┬──────┘
                     │
                     ▼
                 MAC Output
```

The same accumulation structure is used for both multiplier architectures.

## 16-Bit Vedic Multiplier

The Vedic multiplier uses the **Urdhva-Tiryakbhyam (Vertical and Crosswise)** multiplication technique.

The architecture generates cross-products in parallel and combines them using adder circuits to produce the final **32-bit product**.

```text
A[15:0] ──┐
          │
          ▼
   Urdhva-Tiryakbhyam
      Multiplication
          │
          ▼
    Cross Products
          │
          ▼
        Adders
          │
          ▼
      P[31:0]
```

## 16-Bit Radix-4 Booth Multiplier

The Booth multiplier uses **Radix-4 Booth encoding** to reduce the number of partial products generated during multiplication.

The architecture is particularly suitable for signed multiplication and uses additional encoding and arithmetic logic for partial-product generation and accumulation.

```text
A[15:0] ──┐
          │
B[15:0] ──┤
          ▼
    Radix-4 Encoding
          │
          ▼
 Partial Product Generation
          │
          ▼
      Addition Logic
          │
          ▼
      P[31:0]
```

## Design and Verification Flow

```text
Start
  │
  ▼
Verilog HDL Design
  │
  ├── 16-bit Vedic Multiplier
  │
  └── 16-bit Booth Multiplier
  │
  ▼
MAC Integration
  │
  ▼
Testbench Generation
  │
  ▼
Cadence Simulation
  │
  ▼
Waveform Verification
  │
  ▼
Cadence Genus Synthesis
  │
  ▼
Performance Analysis
  │
  ▼
End
```

## Verification

The multiplier architectures were functionally verified using Verilog testbenches and Cadence SimVision waveform analysis.

Example input combinations were used to verify multiplication functionality, including:

```text
0A × 05 = 0032
0C × 0C = 0090
FF × 02 = 01FE
32 × 32 = 0964
```

The Booth architecture was also verified for signed multiplication.

## Synthesis

The designs were synthesized using:

* **Synthesis Tool:** Cadence Genus
* **Technology:** TSMC 180 nm
* **HDL:** Verilog

The synthesis analysis considers:

* Cell area
* Logic cell count
* Power consumption
* Gate-level implementation
* Hardware complexity

## Results

| Parameter                |   Vedic Multiplier | Booth Multiplier |
| ------------------------ | -----------------: | ---------------: |
| Multiplication Technique | Urdhva-Tiryakbhyam |    Radix-4 Booth |
| Technology               |        TSMC 180 nm |      TSMC 180 nm |
| Power                    |   2.05981 × 10⁻⁶ W | 5.52713 × 10⁻⁵ W |
| Synthesized Area         |         76.507 µm² |     1190.851 µm² |
| Logic Cells              |                  7 |               80 |
| Hardware Complexity      |                Low |             High |
| Arithmetic Speed         |               High |         Moderate |
| Switching Activity       |                Low |             High |
| Power Efficiency         |             Better |            Lower |
| Area Efficiency          |             Better |            Lower |

According to the synthesis results, the Vedic multiplier demonstrated lower reported power consumption and synthesized area than the Booth implementation under the evaluated setup.

## Gate-Level Implementation

The synthesized Vedic architecture uses standard cells including:

* AND
* NAND
* NOR
* AOI

The Booth architecture uses a larger collection of standard cells, including:

* AOI
* NAND
* NOR
* XOR
* Inverters
* Multiplexing logic

## Applications

MAC architectures and efficient multiplier implementations are relevant to:

* Digital Signal Processing
* Image Processing
* Communication Systems
* Embedded Systems
* Hardware Accelerators

## Future Scope

Possible extensions include:

* 32-bit and 64-bit MAC architectures
* Further delay optimization
* Lower-power implementations
* FPGA-based validation
* Comparison with Wallace Tree multipliers
* Comparison with Dadda multipliers

## Tools and Technologies

**HDL:** Verilog
**Simulation:** Cadence SimVision
**Synthesis:** Cadence Genus
**Technology Library:** TSMC 180 nm
**Architecture:** MAC
**Multiplier Architectures:** Vedic and Radix-4 Booth
