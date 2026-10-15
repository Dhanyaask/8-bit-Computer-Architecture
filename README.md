# 8-bit ALU-Based CPU (Verilog)

A beginner-friendly Verilog project for an 8-bit ALU-based CPU architecture, intended for simulation and FPGA development.

## Included modules

- `ALU.v` — 8-bit arithmetic and logic operations
- `A_register.v` — accumulator register
- `B_register.v` — B register
- `PC_4bit.v` — 4-bit program counter
- `MAR_4.v` — 4-bit memory address register
- `instruction_register.v` — 8-bit instruction register
- `RAM_16x8.v` — 16 locations × 8-bit RAM
- `Output_register.v` — output register
- `bus.v` — shared 8-bit data bus multiplexer
- `cpu_top.v` — top-level module connecting the components
- `testbench/` — testbenches for ALU, PC, MAR, and bus

## Important integration status

**This package is an initial project bundle, not yet a verified, complete CPU.**

1. `cpu_top.v` instantiates a module named `control_unit`, but no `control_unit.v` implementation was provided in the code collected so far. Add that module before compiling the complete CPU.
2. The ALU instantiation in `cpu_top.v` and the ALU testbench were changed to `ALU` to match the provided `module ALU`.
3. The PC testbench was completed and its instance name was corrected to `PC_4bit`.
4. Reset behavior is not fully consistent across modules: some registers use synchronous reset while others use asynchronous reset. Review this before final FPGA integration.
5. The RAM has no initialization or reset, so its contents may be unknown in simulation until written.
6. The top-level RAM read enable is tied high (`RO = 1'b1`). Confirm this matches the intended control sequence.

## Folder structure

```text
8-bit-ALU-CPU/
├── rtl/
│   ├── ALU.v
│   ├── A_register.v
│   ├── B_register.v
│   ├── PC_4bit.v
│   ├── MAR_4.v
│   ├── instruction_register.v
│   ├── RAM_16x8.v
│   ├── Output_register.v
│   ├── bus.v
│   └── cpu_top.v
├── testbench/
│   ├── ALU8_tb.v
│   ├── PC_4bit_tb.v
│   ├── MAR_4_tb.v
│   └── bus_tb.v
└── README.md
```

## Suggested next steps

1. Implement `control_unit.v`.
2. Simulate each module's testbench.
3. Integrate the modules and verify the instruction/control-signal encoding.
4. Add the FPGA board constraints file and document the board/pin assignments.
5. Commit the project to GitHub after the complete design passes simulation.
