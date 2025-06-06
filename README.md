# 🚀 RISC-V Processor Project (RV32I)

This repository contains two RISC-V CPU implementations based on the **RV32I** instruction set:

- 🧠 **Single-Cycle Core** (`RISC_V_SINGLE_CYCLE_CORE`)  
- ⚙️ **Pipelined Core with Forwarding & Hazard Detection** (`RISC_V_PIPELINE`)  

---

![Pipeline Diagram](FIG01.png)

## 📂 Project Structure

### 📁 `RISC_V_SINGLE_CYCLE_CORE` – 🧠 Single-Cycle CPU
> A basic CPU where each instruction finishes in one clock cycle. Great for beginners to understand datapath and control logic.

🧾 **Core Files**:
- `Single_Cycle_Top.v`: 🔝 Top module
- `Instruction_Memory.v`, `Data_Memory.v`: 🧠 Memory blocks
- `Control_Unit_Top.v`, `ALU.v`, `Register_File.v`: ⚙️ Functional units
- `memfile.hex`: 📜 Program memory (hex file)

---

### 📁 `RISC_V_PIPELINE` – ⚙️ 5-Stage Pipelined CPU
> Advanced design using **IF → ID → EX → MEM → WB** stages with data forwarding and hazard detection.

🧾 **Core Files**:
- Pipeline Stages: `fetch_cycle.v`, `Decode_cycle.v`, `Execute_cycle.v`, `Memory_cycle.v`, `Writeback_cycle.v`
- Hazard Handling: `Hazard_unit.v`
- Top: `Pipeline_top.v`
- Testbench: `Pipeline_top_tb.v`
- Program: `memfile.hex`
- GTKWave Config: `Pipeline_top.gtkw` 🌀

---

## 🛠️ Features

### ✅ RV32I Instruction Support
- 🧮 Arithmetic & Logical Ops
- 🗄️ Load/Store
- 🔀 Branching

### 🧠 Single-Cycle Core
- 1 instruction = 1 clock cycle
- Clean control + datapath integration

### ⚙️ Pipelined Core
- 5 stages: `IF → ID → EX → MEM → WB`
- 🔁 Forwarding Logic (EX/MEM)
- 
---

## 📜 Running the Project

### 🔧 Prerequisites
- Verilog Simulator: **Icarus Verilog**, **ModelSim**, **Vivado**, etc.
- Optional: **GTKWave** for waveform visualization

---

### ▶️ Simulate Single-Cycle Core

```bash
cd RISC_V_SINGLE_CYCLE_CORE/
iverilog -o single_cycle_top.out *.v
vvp single_cycle.out
gtkwave dump.vcd  # 🔍 Optional waveform viewer

cd RISC_V_PIPELINE/
iverilog -o pipeline_top.out *.v
vvp pipeline.out
gtkwave Pipeline_top.gtkw  # 🔍 Optional GTKWave config
```

👨‍💻 Author
Hilay Patel
🎓 [Indian institue of technology, Tirupati]
📧 ee23b066@iittp.ac.in
🌐 [LinkedIn Profile: www.linkedin.com/in/hilay-patel-84a052286]

Thank you for exploring this project! Feel free to fork, use, or contribute. PRs are welcome! 🙌
