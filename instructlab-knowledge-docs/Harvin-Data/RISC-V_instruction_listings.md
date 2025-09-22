# RISC-V instruction listings

The RISC-V instruction set refers to the set of instructions that RISC-V compatible microprocessors support. The instructions are usually part of an executable program, often stored as a computer file and executed on the processor.


## RISC-V Integer Instructions

The table below contains a list of the RV Integer Instructions. The integer instruction set is divided in the base I part of the ISA that comes in a 32 bit RV32 and 64 bit RV64 version and M, B and Zicond extensions. There is also an A extension for atomic instructions and F and D instructions for floating point operations.

# RV Integer (pseudo) Instructions

| Instruction | Name | Format | Extension | RV64 |
|------------|------|--------|-----------|------|
| lb         | Load Byte | rd, imm12(rs) | I |  |
| lh         | Load Half | rd, imm12(rs) | I |  |
| lw         | Load Word | rd, imm12(rs) | I |  |
| ld         | Load Double | rd, imm12(rs) | I | x |
| lbu        | Load Byte (U) | rd, imm12(rs) | I |  |
| lhu        | Load Half (U) | rd, imm12(rs) | I |  |
| lwu        | Load Word (U) | rd, imm12(rs) | I | x |
| sb         | Store Byte | rs1, imm12(rs2) | I |  |
| sh         | Store Half | rs1, imm12(rs2) | I |  |
| sw         | Store Word | rs1, imm12(rs2) | I |  |
| sd         | Store Double | rs1, imm12(rs2) | I | x |
| li         | Load Immediate | rd, imm | I[note 1] |  |
| lui        | Load Upper Immediate | rd, imm20 | I |  |
| auipc      | Add Upper Immediate to Program Counter | rd, imm20 | I |  |
| mv         | MoVe | rd, rs | I[note 2] |  |
| sext.b     | move Sign EXTended least significant Byte | rd, rs | B |  |
| sext.h     | move Sign Extended least significant Half | rd, rs | B |  |
| sext.w     | move Sign EXTended least significant Word | rd, rs | I[note 2] | x |
| zext.b     | move Zero EXTended least significant Byte | rd, rs | I[note 2] |  |
| zext.h     | move Zero EXTended least significant Half | rd, rs | B |  |
| zext.w     | move Zero EXTended least significant Word | rd, rs | B[note 2] | x |
| rev8       | move with REVersed byte order | rd, rs | B |  |
| czero.eqz  | move Conditional on EQual to Zero or ZERO | rd, rs1, rs2 | Zicond |  |
| czero.nez  | move Conditional on Not Equal to Zero or ZERO | rd, rs1, rs2 | Zicond |  |
| addi       | ADD Immediate | rd, rs, imm12 | I |  |
| add        | ADD | rd, rs1, rs2 | I |  |



## Remarks



## See also

