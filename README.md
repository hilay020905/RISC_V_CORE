# RISC-V Processor Project (RV32I)

## Project Overview

This project implements two versions of a RISC-V processor based on the **RV32I** (32-bit Integer Base Instruction Set):

1. **Single-Cycle Core** – A basic implementation that executes one instruction per clock cycle.
2. **Pipelined Core with Hazard Mitigation** – A 5-stage pipelined processor with **data forwarding**.

The processor reads RISC-V machine code from a `.memhex` file using `$readmemh`, enabling simulation of real instruction sequences.

---

## Directory Structure

```bash
├── RISC_V_SINGLE_CYCLE_CORE/
│   ├── datapath.v
│   ├── control_unit.v
│   ├── riscv_single_top.v
│   └── testbench_single.v
│
├── RISC_V_PIPELINE/
│   ├── IF_stage.v
│   ├── ID_stage.v
│   ├── EX_stage.v
│   ├── MEM_stage.v
│   ├── WB_stage.v
│   ├── forwarding_unit.v
│   ├── hazard_detection.v
│   ├── riscv_pipeline_top.v
│   └── testbench_pipeline.v
│
├── programs/
│   └── sample_program.mem   # RISC-V machine code (hex)
│
├── docs/
│   └── architecture_diagram.pdf
│
└── README.md

---

## Features

### ✅ Single-Cycle Core
- Supports the **RV32I** base integer instruction set
- Executes each instruction in a single clock cycle
- Simple datapath and control logic

### ✅ Pipelined Core
- Implements a 5-stage pipeline: **IF → ID → EX → MEM → WB**
- Includes **forwarding unit** to handle data hazards (EX–EX, MEM–EX)
- Includes **hazard detection unit** to insert stalls when needed
- Basic **branch flushing** logic included

---

## Hazard Handling

- **Data Hazards**:  
  Resolved using forwarding paths between pipeline stages.

- **Control Hazards**:  
  Basic flushing of incorrect instructions after a branch is taken.

- **Structural Hazards**:  
  Avoided by careful design (single-port memory assumed with dual-stage access handling).

---

## How to Run the Simulation

### Prerequisites

- Verilog simulator: **Icarus Verilog**, **ModelSim**, or **Vivado**
- Optional: **GTKWave** for waveform analysis

### Program Loading Format

The processor loads machine code using Verilog's `$readmemh("program.memhex")` function from the `programs/` directory.

Ensure your memory modules include:
```verilog
$readmemh("programs/program.memhex", memory_array);

cd single_core/
iverilog -o single.vvp *.v
vvp single.vvp
gtkwave dump.vcd  # (Optional) to view waveform
cd pipeline_core/
iverilog -o pipeline.vvp *.v
vvp pipeline.vvp
gtkwave dump.vcd  # (Optional) to view waveform
