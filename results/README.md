# Design and Performance Analysis of 8-Bit Vedic and Booth Multipliers Using MAC Unit

## Overview

This project focuses on the design and performance analysis of **8-bit Vedic and Booth multiplier architectures integrated with a Multiply-Accumulate (MAC) unit**.

The objective is to compare the two multiplier architectures in terms of hardware complexity, area utilization, power consumption, and arithmetic performance.

The designs are described using **Verilog HDL** and evaluated using a VLSI design flow involving **Cadence simulation and synthesis tools**.

## Objective

The main objective of this project is to investigate the suitability of Vedic and Booth multiplication techniques for efficient MAC-based arithmetic hardware.

The comparison focuses on:

* Power consumption
* Synthesized area
* Logic cell utilization
* Hardware complexity
* Arithmetic performance
* Switching activity

## MAC Architecture

The MAC unit performs the operation:

```text
MAC = (A × B) + Accumulator
```

The architecture consists of:

```text
Input A ─────┐
             │
Input B ─────┤
             ▼
       ┌─────────────┐
       │  Multiplier │
       └──────┬──────┘
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

Two versions of the MAC architecture are implemented using different multiplier architectures.

## Vedic Multiplier

The Vedic multiplier uses the **Urdhva-Tiryakbhyam (Vertical and Crosswise)** multiplication technique.

The architecture generates multiplication terms using the Vedic multiplication approach and combines them through addition logic to obtain the multiplication result.

```text
Input A
   │
   ├──────────────┐
   │              │
Input B           │
   │              ▼
   └──────► Urdhva-Tiryakbhyam
                  │
                  ▼
             Partial Products
                  │
                  ▼
                Adders
                  │
                  ▼
               Product
```

## Booth Multiplier

The Booth multiplier uses **Booth recoding** to reduce the number of partial products involved in multiplication.

The architecture performs recoding and partial-product generation before the arithmetic addition stage.

```text
Input A
   │
Input B
   │
   ▼
Booth Recoding
   │
   ▼
Partial Product Generation
   │
   ▼
Addition
   │
   ▼
Product
```

## Comparison Methodology

Both multiplier architectures are integrated into MAC units using a common accumulation structure.

This provides a common basis for comparing the hardware characteristics of the Vedic and Booth implementations.

```text
             ┌── Vedic Multiplier ──┐
Inputs ──────┤                      ├── Adder ── Accumulator
             └── Booth Multiplier ──┘
```

## Design Flow

```text
Verilog HDL Design
        │
        ▼
Vedic / Booth Multiplier
        │
        ▼
MAC Integration
        │
        ▼
Testbench Development
        │
        ▼
Cadence Simulation
        │
        ▼
Waveform Verification
        │
        ▼
Cadence Synthesis
        │
        ▼
Area / Power / Cell Analysis
        │
        ▼
Performance Comparison
```

## Verification

The multiplier architectures were functionally verified using Verilog testbenches and Cadence simulation.

Simulation waveforms were analyzed to verify the multiplication functionality and arithmetic operation of the designs.

## VLSI Implementation

The designs were synthesized using the Cadence Genus environment with the TSMC 180 nm technology library used in the project.

The synthesis analysis included:

* Standard-cell utilization
* Synthesized area
* Power consumption
* Gate-level implementation
* Hardware complexity

## Performance Results

| Parameter                |              Vedic |            Booth |
| ------------------------ | -----------------: | ---------------: |
| Multiplication Technique | Urdhva-Tiryakbhyam |            Booth |
| Technology Library       |        TSMC 180 nm |      TSMC 180 nm |
| Power Consumption        |   2.05981 × 10⁻⁶ W | 5.52713 × 10⁻⁵ W |
| Synthesized Area         |             76.507 |         1190.851 |
| Logic Cells              |                  7 |               80 |
| Hardware Complexity      |                Low |             High |
| Arithmetic Speed         |               High |         Moderate |
| Switching Activity       |                Low |             High |
| Power Efficiency         |             Better |            Lower |
| Area Efficiency          |             Better |            Lower |

## Simulation Results

### Vedic Multiplier

Add the Cadence SimVision waveform here.

```text
simulation/vedic_waveform.png
```

### Booth Multiplier

Add the Cadence SimVision waveform here.

```text
simulation/booth_waveform.png
```

## Synthesis Results

The synthesized designs were analyzed using Cadence Genus.

The project includes gate-level schematic, area, power, and cell-utilization results for both multiplier architectures.

## Applications

MAC-based arithmetic units are widely relevant to:

* Digital Signal Processing
* Image Processing
* Communication Systems
* Embedded Systems
* Hardware Accelerators

## Future Scope

Possible extensions of this work include:

* Higher-bit-width multiplier architectures
* Delay optimization
* Power optimization
* FPGA-based validation
* Comparison with Wallace Tree multipliers
* Comparison with Dadda multipliers

## Tools and Technologies

* Verilog HDL
* Cadence SimVision
* Cadence Genus
* TSMC 180 nm Technology Library
* VLSI Design
* Digital Arithmetic
* MAC Architecture
