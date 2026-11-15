# 32-bit MIPS Processor Design in VHDL

## Overview

This project presents the design and simulation of a **32-bit MIPS processor** using VHDL. It explores two processor architectures:

- **Single-Cycle Architecture**
- **Multi-Cycle Architecture**

The objective is to understand the internal organization of a processor, the execution of MIPS instructions, and the role of its main hardware components.

Both architectures were described in VHDL and tested through simulation using **Quartus Prime**.

## Project Objectives

- Design a 32-bit MIPS processor using VHDL.
- Implement and compare single-cycle and multi-cycle architectures.
- Understand the processor datapath and control unit.
- Implement the main components required for instruction execution.
- Simulate the processor and verify its behavior using waveform analysis.

## Processor Architectures

### 1. Single-Cycle Architecture

The single-cycle processor executes each instruction in one clock cycle.

All operations required by an instruction, including instruction fetch, decoding, execution, memory access, and write-back, are completed within that cycle.

**Main characteristics:**
- One clock cycle per instruction.
- A relatively simple control structure.
- Instruction execution is performed through a single datapath.
- The clock period must accommodate the slowest instruction.

### 2. Multi-Cycle Architecture

The multi-cycle processor divides instruction execution into several stages. Each stage is performed in a separate clock cycle, allowing hardware resources to be reused.

The control unit is implemented as a **Finite State Machine (FSM)** that generates the control signals required for each execution stage.

The main execution stages are:

1. **Instruction Fetch (IF):** Fetches the instruction from instruction memory.
2. **Instruction Decode (ID):** Decodes the instruction and reads the required registers.
3. **Execute (EX):** Performs the arithmetic or logical operation, calculates an address, or evaluates a branch.
4. **Memory Access (MEM):** Reads from or writes to data memory when required.
5. **Write Back (WB):** Writes the result back into the register file when required.

**Main characteristics:**
- Instructions require different numbers of clock cycles.
- Hardware resources can be shared between execution stages.
- The control unit manages execution through an FSM.
- The clock period can be shorter than in a single-cycle implementation.

## Main Components

The processor is composed of several interconnected hardware modules.

| Component | Description |
|---|---|
| Program Counter (PC) | Stores the address of the current instruction. |
| Instruction Memory | Stores the program instructions. |
| Register File | Contains the processor's general-purpose registers. |
| ALU | Performs arithmetic and logical operations. |
| ALU Control Unit | Determines the operation performed by the ALU. |
| Main Control Unit | Generates the control signals for instruction execution. |
| Data Memory | Stores and retrieves data. |
| Multiplexers | Select between different datapath inputs. |
| Sign Extension Unit | Extends immediate values to 32 bits. |
| Shift Units | Perform the required shift operations. |
| Instruction Register | Stores the current instruction in the multi-cycle architecture. |

Additional temporary registers are used in the multi-cycle architecture to store intermediate values between execution stages.

## Supported Instructions

The processor implements instructions from the main MIPS instruction formats.

### R-Type Instructions

R-type instructions perform register-to-register operations.

Examples:
- `add`
- `sub`
- `and`
- `or`
- `slt`

### I-Type Instructions

I-type instructions use an immediate value or access memory.

Examples:
- `addi`
- `lw`
- `sw`
- `beq`

### J-Type Instructions

J-type instructions are used for jump operations.

Example:
- `j`

## Control Unit

The control unit coordinates the processor's internal operations by generating the appropriate control signals.

For the multi-cycle architecture, the control unit is implemented as a finite state machine.

The main control signals include:

- `RegDst`
- `RegWrite`
- `ALUSrcA`
- `ALUSrcB`
- `ALUOp`
- `PCSource`
- `PCWriteCond`
- `PCWrite`
- `IorD`
- `MemRead`
- `MemWrite`
- `MemtoReg`
- `IRWrite`

These signals control register operations, ALU inputs, memory access, instruction loading, and program counter updates.

## Simulation and Verification

The processor designs were simulated using **Quartus Prime**.

Simulation waveforms were used to verify the behavior of the different components and confirm that instructions were executed as expected.

The repository includes:

- The architecture diagram of the single-cycle processor.
- The simulation waveform of the single-cycle processor.
- The architecture diagram of the multi-cycle processor.
- The simulation waveform of the multi-cycle processor.

These diagrams and waveforms illustrate the internal organization and operation of both processor architectures.

## Architecture Diagrams and Simulation Results

### Single-Cycle Architecture

The following diagram illustrates the datapath and main components of the single-cycle processor.
<img width="1280" height="758" alt="image" src="https://github.com/user-attachments/assets/d2ac6bfd-ea24-408b-89e1-ab44e68abbfb" />

The corresponding simulation waveform demonstrates its operation during instruction execution.
<img width="1280" height="216" alt="image" src="https://github.com/user-attachments/assets/0a7cd4a1-576d-4bdb-9bc5-3dead358feb0" />

### Multi-Cycle Architecture

The following diagram illustrates the datapath and control structure of the multi-cycle processor.
<img width="1280" height="700" alt="image" src="https://github.com/user-attachments/assets/443e9d9f-e1fc-45cd-88f8-1028a14e61df" />

The corresponding simulation waveform shows the different execution stages and the control signals generated by the FSM.
<img width="1280" height="411" alt="image" src="https://github.com/user-attachments/assets/1b19391d-dcac-431d-9044-0cdcc9cd610a" />

## Single-Cycle vs Multi-Cycle Comparison

| Feature | Single-Cycle | Multi-Cycle |
|---|---|---|
| Instruction execution | One clock cycle | Multiple clock cycles |
| Control unit | Combinational control | FSM-based control |
| Hardware usage | More dedicated resources | Resources can be shared |
| Clock period | Depends on the slowest instruction | Depends on the longest execution stage |
| Execution time per instruction | Fixed | Variable |
| Design complexity | Simpler control structure | More complex control structure |

## Tools and Technologies

- **VHDL** – Hardware description language.
- **Quartus Prime** – Design, compilation, and simulation environment.
- **ModelSim / Questa** – Waveform simulation and verification, if used in the project.

## Repository Structure

```text
Design-of-a-32-bits--MIPS-Processor-in-VHDL/
│
├── Single_Cycle/
│   ├── VHDL source files
│   └── Simulation files
│
├── Multi_Cycle/
│   ├── VHDL source files
│   └── Simulation files
│
├── README.md
└── ...
```

*Note: The directory names above are illustrative. Adjust them to match the actual repository structure.*

## Conclusion

This project demonstrates the design and simulation of two 32-bit MIPS processor architectures using VHDL.

Implementing both single-cycle and multi-cycle processors provides a practical understanding of processor datapaths, control units, instruction execution, and hardware resource management.

The simulation results help verify the functionality of both architectures and highlight the main differences between their implementations.

---

**Project:** 32-bit MIPS Processor Design in VHDL  
**Language:** VHDL  
**Architectures:** Single-Cycle and Multi-Cycle







