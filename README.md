# RISC_V_CORE
RISC-V implementation with Single Cycle and Pipeline cores in Verilog
# RISC-V Core Implementations

This repository contains Verilog implementations of:
- ✅ RISC-V Single Cycle Core
- 🚀 RISC-V 5-Stage Pipelined Core

## Directory Structure

- `SingleCycle/` – RISC-V Single Cycle Core
- `Pipeline/` – RISC-V Pipelined Core

## How to Run

Use any Verilog simulator like Iverilog, ModelSim, etc and GTKWave based waveform viewer

```bash
cd SingleCycle
iverilog -o cpu_test *.v
./cpu_test
