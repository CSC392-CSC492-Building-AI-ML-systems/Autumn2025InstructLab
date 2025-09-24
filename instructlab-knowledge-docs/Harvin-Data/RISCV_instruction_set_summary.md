Appendix B.  RISC-V Instruction Set Summary
Figure B.1 RISC-V 32-bit instruction formats
Table B.1 RV32I: RISC-V integer instructions
op funct3 funct7 Type Instruction Description Operation
0000011 (3) 000 – Ilb    rd,  imm(rs1) load byte rd =  SignExt([Address] 7:0)
0000011 (3) 001 – Ilh    rd,  imm(rs1) load half rd =  SignExt([Address] 15:0)
0000011 (3) 010 – Ilw    rd,  imm(rs1) load word rd =          [Address] 31:0
0000011 (3) 100 – Ilbu   rd,  imm(rs1) load byte unsigned rd =  ZeroExt([Address] 7:0)
0000011 (3) 101 – Ilhu   rd,  imm(rs1) load half unsigned rd =  ZeroExt([Address] 15:0)
0010011 (19) 000 – Iaddi  rd,  rs1, imm add immediate rd =  rs1 +   SignExt(imm)
0010011 (19) 001 0000000*Islli  rd,  rs1, uimm shift left logical immediate rd =  rs1 <<  uimm
0010011 (19) 010 – Islti  rd,  rs1, imm set less than immediate rd = (rs1 <   SignExt(imm))
0010011 (19) 011 – Isltiu rd,  rs1, imm set less than imm. unsigned rd = (rs1 <   SignExt(imm))
0010011 (19) 100 – Ixori  rd,  rs1, imm xor immediate rd =  rs1 ^   SignExt(imm)
0010011 (19) 101 0000000*Isrli  rd,  rs1, uimm shift right logical immediate rd =  rs1 >>  uimm
0010011 (19) 101 0100000*Israi  rd,  rs1, uimm shift right arithmetic imm. rd =  rs1 >>> uimm
0010011 (19) 110 – Iori   rd,  rs1, imm or immediate rd =  rs1 |   SignExt(imm)
0010011 (19) 111 – Iandi  rd,  rs1, imm and immediate rd =  rs1 &   SignExt(imm)
0010111 (23) – – Uauipc rd,  upimm add upper immediate to PC rd = {upimm, 12 'b0} + PC 
0100011 (35) 000 – Ssb    rs2, imm(rs1) store byte [Address] 7:0 = rs2 7:0
0100011 (35) 001 – Ssh    rs2, imm(rs1) store half [Address] 15:0 = rs215:0
0100011 (35) 010 – Ssw    rs2, imm(rs1) store word [Address] 31:0 = rs2
0110011 (51) 000 0000000 Radd   rd,  rs1, rs2 add rd =  rs1 +   rs2
0110011 (51) 000 0100000 Rsub   rd,  rs1, rs2 sub rd =  rs1 —   rs2
0110011 (51) 001 0000000 Rsll   rd,  rs1, rs2 shift left logical rd =  rs1 <<  rs2 4:0
0110011 (51) 010 0000000 Rslt   rd,  rs1, rs2 set less than rd = (rs1 <   rs2)
0110011 (51) 011 0000000 Rsltu  rd,  rs1, rs2 set less than unsigned rd = (rs1 <   rs2)
0110011 (51) 100 0000000 Rxor   rd,  rs1, rs2 xor rd =  rs1 ^   rs2
0110011 (51) 101 0000000 Rsrl   rd,  rs1, rs2 shift right logical rd =  rs1 >>  rs2 4:0
0110011 (51) 101 0100000 Rsra   rd,  rs1, rs2 shift right arithmetic rd =  rs1 >>> rs2 4:0
0110011 (51) 110 0000000 Ror    rd,  rs1, rs2 or rd =  rs1 |   rs2
0110011 (51) 111 0000000 Rand   rd,  rs1, rs2 and rd =  rs1 &   rs2
0110111 (55) – – Ului   rd,  upimm load upper immediate rd = {upimm, 12’b0}
1100011 (99) 000 – Bbeq   rs1, rs2, label branch if = if (rs1 == rs2) PC = BTA
1100011 (99) 001 – Bbne   rs1, rs2, label branch if ≠ if (rs1 ≠  rs2) PC = BTA
1100011 (99) 100 – Bblt   rs1, rs2, label branch if < if (rs1 <  rs2) PC = BTA
1100011 (99) 101 – Bbge   rs1, rs2, label branch if ≥ if (rs1 ≥  rs2) PC = BTA
1100011 (99) 110 – Bbltu  rs1, rs2, label branch if < unsigned if (rs1 <  rs2) PC = BTA
1100011 (99) 111 – Bbgeu  rs1, rs2, label branch if ≥ unsigned if (rs1 ≥  rs2) PC = BTA
1100111 (103) 000 – Ijalr  rd,  rs1, imm jump and link register PC = rs1 + SignExt(imm), rd = PC  + 4
1101111 (111) – – Jjal   rd,  label jump and link PC = JTA,                rd = PC  + 4• imm :  signed immediate in imm 11:0
• uimm :  5-bit unsigned immediate in imm 4:0
• upimm :  20 upper bits of a 32-bit immediate, in imm 31:12
• Address :  memory address: rs1 + SignExt( imm 11:0)
• [Address] :  data at memory location Address
• BTA :  branch target address: PC + SignExt({ imm 12:1, 1'b0})
• JTA :  j ump target address: PC + SignExt({ imm 20:1, 1'b0})
• label :  text indicating instruction address
• SignExt : value sign-extended to 32 bits
• ZeroExt : value zero-extended to 32 bits
• csr:   control and status register
    *encoded in instr 31:25, the upper seven bits of the immediate field

Table B.2 RV64I: Extra integer instructions
op funct3 funct7 Type Instruction Description Operation
0000011 (3) 011 – Ild    rd,  imm(rs1) load double word rd = [Address] 63:0
0000011 (3) 110 – Ilwu   rd,  imm(rs1) load word unsigned rd = ZeroExt([Address] 31:0)
0011011 (27) 000 – Iaddiw rd,  rs1, imm add immediate word rd = SignExt((rs1  + SignExt(imm)) 31:0)
0011011 (27) 001 0000000 Islliw rd,  rs1, uimm shift left logical immediate word rd = SignExt((rs1 31:0 <<  uimm) 31:0) 
0011011 (27) 101 0000000 Isrliw rd,  rs1, uimm shift right logical immediate word rd = SignExt((rs1 31:0 >>  uimm) 31:0) 
0011011 (27) 101 0100000 Israiw rd,  rs1, uimm shift right arith. immediate word rd = SignExt((rs1 31:0 >>>  uimm) 31:0)
0100011 (35) 011 – Ssd    rs2,  imm(rs1) store double word [Address] 63:0 = rs2
0111011 (59) 000 0000000 Raddw  rd,  rs1, rs2 add word rd = SignExt((rs1  + rs2)31:0)
0111011 (59) 000 0100000 Rsubw  rd,  rs1, rs2 subtract word rd = SignExt((rs1  — rs2)31:0)
0111011 (59) 001 0000000 Rsllw  rd,  rs1, rs2 shift left logical word rd = SignExt((rs1 31:0 <<  rs24:0)31:0) 
0111011 (59) 101 0000000 Rsrlw  rd,  rs1, rs2 shift right logical word rd = SignExt((rs1 31:0 >>  rs24:0)31:0) 
0111011 (59) 101 0100000 Rsraw  rd,  rs1, rs2 shift right arithmetic word rd = SignExt((rs1 31:0 >>>  rs24:0)31:0)
Table B.3 RVF/D: RISC-V single- and double-precision floating-point instructions
op funct3 funct7 rs2 Type Instruction Description Operation
1000011 (67) rm fs3,      fmt – R4fmadd  fd,fs1,fs2,fs3 multiply-add fd =   fs1 * fs2 + fs3
1000111 (71) rm fs3,      fmt – R4fmsub  fd,fs1,fs2,fs3 multiply-subtract fd =   fs1 * fs2 — fs3
1001011 (75) rm fs3,      fmt – R4fnmsub fd,fs1,fs2,fs3 negate multiply-add fd = —(fs1 * fs2 + fs3)
1001111 (79) rm fs3,      fmt – R4fnmadd fd,fs1,fs2,fs3 negate multiply-subtract fd = —(fs1 * fs2 – fs3)
1010011 (83) rm 00000, fmt – Rfadd   fd,fs1,fs2 add fd =   fs1 + fs2
1010011 (83) rm 00001, fmt – Rfsub   fd,fs1,fs2 subtract fd =   fs1 — fs2
1010011 (83) rm 00010, fmt – Rfmul   fd,fs1,fs2 multiply fd =   fs1 * fs2
1010011 (83) rm 00011, fmt – Rfdiv   fd,fs1,fs2 divide fd =   fs1 / fs2
1010011 (83) rm 01011, fmt 00000 Rfsqrt  fd,fs1 square root fd = sqrt(fs1)
1010011 (83) 000 00100, fmt – Rfsgnj  fd,fs1,fs2 sign injection fd = fs1, sign =  sign(fs2)
1010011 (83) 001 00100, fmt – Rfsgnjn fd,fs1,fs2 negate sign injection fd = fs1, sign = —sign(fs2)
1010011 (83) 010 00100, fmt – Rfsgnjx fd,fs1,fs2 xor sign injection fd = fs1,
sign = sign(fs2)  ^ sign(fs1) 
1010011 (83) 000 00101, fmt – Rfmin   fd,fs1,fs2 min fd = min(fs1, fs2)
1010011 (83) 001 00101, fmt – Rfmax   fd,fs1,fs2 max fd = max(fs1, fs2)
1010011 (83) 010 10100, fmt – Rfeq    rd,fs1,fs2 compare = rd = (fs1 == fs2)
1010011 (83) 001 10100, fmt – Rflt    rd,fs1,fs2 compare < rd = (fs1 <  fs2)
1010011 (83) 000 10100, fmt – Rfle    rd,fs1,fs2 compare ≤ rd = (fs1 ≤     fs2)
1010011 (83) 001 11100, fmt 00000 Rfclass rd,fs1 classify rd = classification of fs1
RVF only
0000111 (7) 010 – – Iflw       fd, imm(rs1) load float fd = [Address] 31:0
0100111 (39) 010 – – Sfsw       fs2,imm(rs1) store float [Address] 31:0 = fd
1010011 (83) rm 1100000 00000 Rfcvt.w.s  rd, fs1 convert to integer rd = integer(fs1)
1010011 (83) rm 1100000 00001 Rfcvt.wu.s rd, fs1 convert to unsigned integer rd = unsigned(fs1)
1010011 (83) rm 1101000 00000 Rfcvt.s.w  fd, rs1 convert int to float fd = float(rs1)
1010011 (83) rm 1101000 00001 Rfcvt.s.wu fd, rs1 convert unsigned to float fd = float(rs1)
1010011 (83) 000 1110000 00000 Rfmv.x.w   rd, fs1 move to integer register rd = fs1
1010011 (83) 000 1111000 00000 Rfmv.w.x   fd, rs1 move to f.p. register fd = rs1
RVD only
0000111 (7) 011 – – Ifld       fd, imm(rs1) load double fd = [Address] 63:0
0100111 (39) 011 – – Sfsd       fs2,imm(rs1) store double [Address] 63:0 = fd
1010011 (83) rm 1100001 00000 Rfcvt.w.d  rd, fs1 convert to integer rd = integer(fs1)
1010011 (83) rm 1100001 00001 Rfcvt.wu.d rd, fs1 convert to unsigned integer rd = unsigned(fs1)
1010011 (83) rm 1101001 00000 Rfcvt.d.w  fd, rs1 convert int to double fd = double(rs1)
1010011 (83) rm 1101001 00001 Rfcvt.d.wu fd, rs1 convert unsigned to double fd = double(rs1)
1010011 (83) rm 0100000 00001 Rfcvt.s.d  fd, fs1   convert double to float fd = float(fs1)
1010011 (83) rm 0100001 00000 Rfcvt.d.s  fd, fs1 convert float to double fd = double(fs1)
fs1, fs2, fs3, fd: floating-point registers. fs1, fs2, and fd are encoded in fields rs1, rs2, and rd; only R4-type also encodes fs3.  fmt: precision of computational 
instruction (single=00 2, double=01 2, quad=11 2). rm: rounding mode (0=to nearest, 1=toward zero, 2=down, 3=up, 4=to nearest (max magnitude), 7=dynamic). 
sign( fs1): the sign of fs1.In RV64I, registers are 64 bits, but instructions are still 32 bits. The term “word” generally refers to a 32-bit value. In RV64I, immediate shift instructions use 
6-bit immediates: uimm 5:0; but for word shifts, the most significant bit of the shift amount (uimm 5) must be 0. Instructions ending in “w” (for “word”) operate 
on the lower half of the 64-bit registers. Sign- or zero-extension produces a 64-bit result.

Table B.4 Register names and numbers
NameRegister 
Number Use
zero x0 Constant value 0
ra x1 Return address
sp x2 Stack pointer
gp x3 Global pointer
tp x4 Thread pointer
t0  –2 x5  –7 Temporary registers
s0/fp x8 Saved register / Frame pointer
s1 x9 Saved register
a0  –1 x10  –11 Function arguments / Return values
a2  –7 x12  –17 Function arguments
s2  –11 x18  –27 Saved registers
t3-6 x28 –31 Temporary registersFigure B.2 RISC-V compressed (16-bit) instruction formats
Table B.6 RVC: RISC-V compressed (16-bit) instructions
op instr 15:10 funct2 Type RVC Instruction 32-Bit Equivalent
00 (0) 000 – – – – CIW c.addi4spn rd', sp, imm addi rd',  sp,  ZeroExt(imm) *4
00 (0) 001 – – – – CL c.fld   fd',    imm(rs1') fld  fd',  (ZeroExt(imm) *8)(rs1')
00 (0) 010 – – – – CL c.lw    rd',    imm(rs1') lw   rd',  (ZeroExt(imm) *4)(rs1')
00 (0) 011 – – – – CL c.flw   fd',    imm(rs1') flw  fd',  (ZeroExt(imm) *4)(rs1')
00 (0) 101 – – – – CS c.fsd   fs2',   imm(rs1') fsd  fs2', (ZeroExt(imm) *8)(rs1')
00 (0) 110 – – – – CS c.sw    rs2',   imm(rs1') sw   rs2', (ZeroExt(imm) *4)(rs1')
00 (0) 111 – – – – CS c.fsw   fs2',   imm(rs1') fsw  fs2', (ZeroExt(imm) *4)(rs1')
01 (1) 000000 – CI c.nop                 (rs1=0,imm=0) nop
01 (1) 000 – – – – CI c.addi  rd,     imm addi rd,   rd,  SignExt(imm)
01 (1) 001 – – – – CJ c.jal   label jal  ra,   label
01 (1) 010 – – – – CI c.li    rd,     imm addi rd,   x0,  SignExt(imm)
01 (1) 011 – – – – CI c.lui   rd,     imm lui  rd,   {14{imm 5}, imm}
01 (1) 011 – – – – CI c.addi16sp sp,  imm addi sp,   sp,  SignExt(imm) *16
01 (1) 100  –  00 – CB' c.srli  rd',    imm srli rd',  rd', imm
01 (1) 100  –  01 – CB' c.srai  rd',    imm srai rd',  rd', imm
01 (1) 100  –  10 – CB' c.andi  rd',    imm andi rd',  rd', SignExt(imm)
01 (1) 100011 00 CS' c.sub   rd',    rs2' sub  rd',  rd', rs2'
01 (1) 100011 01 CS' c.xor   rd',    rs2' xor  rd',  rd', rs2'
01 (1) 100011 10 CS' c.or    rd',    rs2' or   rd',  rd', rs2'
01 (1) 100011 11 CS' c.and   rd',    rs2' and  rd',  rd', rs2'
01 (1) 101 – – – – CJ c.j     label jal  x0,   label
01 (1) 110 – – – – CB c.beqz  rs1',   label beq  rs1', x0,  label
01 (1) 111 – – – – CB c.bnez  rs1',   label bne  rs1', x0,  label
10 (2) 000 – – – – CI c.slli  rd,     imm slli rd,   rd,  imm
10 (2) 001 – – – – CI c.fldsp fd,     imm fld  fd,   (ZeroExt(imm) *8)(sp)
10 (2) 010 – – – – CI c.lwsp  rd,     imm lw   rd,   (ZeroExt(imm) *4)(sp)
10 (2) 011 – – – – CI c.flwsp fd,     imm flw  fd,   (ZeroExt(imm) *4)(sp)
10 (2) 1000 – – – CR c.jr    rs1           (rs1≠0,rs2=0) jalr x0,   rs1, 0
10 (2) 1000 – – – CR c.mv    rd,     rs2   (rd ≠0,rs2≠0) add  rd,   x0,  rs2
10 (2) 1001 – – – CR c.ebreak              (rs1=0,rs2=0) ebreak
10 (2) 1001 – – – CR c.jalr  rs1           (rs1≠0,rs2=0) jalr ra,   rs1, 0
10 (2) 1001 – – – CR c.add   rd,     rs2   (rs1≠0,rs2≠0) add  rd,   rd,  rs2
10 (2) 101 – – – – CSS c.fsdsp fs2,    imm fsd  fs2,  (ZeroExt(imm) *8)(sp)
10 (2) 110 – – – – CSS c.swsp  rs2,    imm sw   rs2,  (ZeroExt(imm) *4)(sp)
10 (2) 111 – – – – CSS c.fswsp fs2,    imm fsw  fs2,  (ZeroExt(imm) *4)(sp)
rs1', rs2', rd': 3-bit register designator for registers 8  –15: 000 2 = x8 or f8, 001 2 = x9 or f9, etc.Table B.5 RVM: RISC-V multiply and divide instructions
op funct3 funct7 Type Instruction Description Operation
0110011 (51) 000 0000001 Rmul    rd, rs1, rs2 multiply rd = (rs1 * rs2) 31:0
0110011 (51) 001 0000001 Rmulh   rd, rs1, rs2 multiply high signed signed rd = (rs1 * rs2) 63:32
0110011 (51) 010 0000001 Rmulhsu rd, rs1, rs2 multiply high signed unsigned rd = (rs1 * rs2) 63:32
0110011 (51) 011 0000001 Rmulhu  rd, rs1, rs2 multiply high unsigned unsigned rd = (rs1 * rs2) 63:32
0110011 (51) 100 0000001 Rdiv    rd, rs1, rs2 divide (signed) rd =  rs1 / rs2
0110011 (51) 101 0000001 Rdivu   rd, rs1, rs2 divide unsigned rd =  rs1 / rs2
0110011 (51) 110 0000001 Rrem    rd, rs1, rs2 remainder (signed) rd =  rs1 % rs2
0110011 (51) 111 0000001 Rremu   rd, rs1, rs2 remainder unsigned rd =  rs1 % rs2


Table B.7 RISC-V pseudoinstructions 
Pseudoinstruction RISC-V Instructions Description Operation
nop addi  x0,  x0,  0 no operation
li   rd,  imm 11:0 addi  rd,  x0,  imm 11:0 load 12-bit immediate rd =  SignExtend(imm 11:0)
li   rd,  imm 31:0 lui   rd,  imm 31:12*
addi  rd,  rd,  imm 11:0load 32-bit immediate rd =  imm 31:0
mv   rd,  rs1 addi  rd,  rs1, 0 move (also called “register copy”) rd =  rs1
not  rd,  rs1 xori  rd,  rs1, —1 one’s complement rd = ~rs1
neg  rd,  rs1 sub   rd,  x0,  rs1 two’s complement rd = —rs1
seqz rd,  rs1 sltiu rd,  rs1, 1 set if = 0 rd = (rs1 == 0)
snez rd,  rs1 sltu  rd,  x0,  rs1 set if ≠ 0 rd = (rs1 ≠  0)
sltz rd,  rs1 slt   rd,  rs1, x0 set if < 0 rd = (rs1 <  0)
sgtz rd,  rs1 slt   rd,  x0,  rs1 set if > 0 rd = (rs1 >  0)
beqz rs1, label beq   rs1, x0,  label branch if = 0 if (rs1 == 0)   PC = label
bnez rs1, label bne   rs1, x0,  label branch if ≠ 0 if (rs1 ≠  0)   PC = label
blez rs1, label bge   x0,  rs1, label branch if ≤ 0 if (rs1 ≤  0)   PC = label
bgez rs1, label bge   rs1, x0,  label branch if ≥ 0 if (rs1 ≥  0)   PC = label
bltz rs1, label blt   rs1, x0,  label branch if < 0 if (rs1 <  0)   PC = label
bgtz rs1, label blt   x0,  rs1, label branch if > 0 if (rs1 >  0)   PC = label
ble  rs1, rs2, label bge   rs2, rs1, label branch if ≤ if (rs1 ≤  rs2) PC = label
bgt  rs1, rs2, label blt   rs2, rs1, label branch if > if (rs1 >  rs2) PC = label
bleu rs1, rs2, label bgeu  rs2, rs1, label branch if ≤ (unsigned) if (rs1 ≤  rs2) PC = label
bgtu rs1, rs2, label bltu  rs2, rs1, offset branch if > (unsigned) if (rs1 >  rs2) PC = label
j    label jal   x0,  label jump PC = label
jal  label jal   ra,  label jump and link PC = label,       ra = PC + 4
jr   rs1 jalr  x0,  rs1, 0 jump register PC = rs1
jalr rs1 jalr  ra,  rs1, 0 jump and link register PC = rs1,         ra = PC + 4
ret jalr  x0,  ra,  0 return from function PC = ra
call label jal   ra,  label call nearby function PC = label,       ra = PC + 4
call label auipc ra,  offset 31:12*
jalr  ra,  ra, offset 11:0call far away function PC = PC + offset, ra = PC + 4
la       rd,  symbol auipc rd,  symbol 31:12*
addi  rd,  rd,  symbol 11:0load address of global variable rd =  PC + symbol
l{b|h|w} rd,  symbol auipc    rd,  symbol 31:12*
l{b|h|w} rd,  symbol 11:0(rd)load global variable rd = [PC + symbol]
s{b|h|w} rs2, symbol, rs1 auipc    rs1, symbol 31:12*
s{b|h|w} rs2, symbol 11:0(rs1)store global variable [PC + symbol] = rs2
csrr rd,  csr csrrs rd,  csr, x0 read  CSR rd = csr
csrw csr, rs1 csrrw x0,  csr, rs1 write CSR csr = rs1
op funct3 Type Instruction Description Operation
1110011 (115) 000 Iecall transfer control to OS                  (imm=0)
1110011 (115) 000 Iebreak transfer control to debugger         (imm=1)
1110011 (115) 000 Iuret return from user exception           (rs1=0,rd=0,imm=2) PC = uepc
1110011 (115) 000 Isret return from supervisor exception   (rs1=0,rd=0,imm=258) PC = sepc
1110011 (115) 000 Imret return from machine exception     (rs1=0,rd=0,imm=770) PC = mepc
1110011 (115) 001 Icsrrw  rd,csr,rs1 CSR read/write                             (imm=CSR number) rd = csr,csr  = rs1
1110011 (115) 010 Icsrrs  rd,csr,rs1 CSR read/set                                 (imm=CSR number) rd = csr,csr  = csr |   rs1
1110011 (115) 011 Icsrrc  rd,csr,rs1 CSR read/clear                              (imm=CSR number) rd = csr,csr  = csr & ~rs1
1110011 (115) 101 Icsrrwi rd,csr,uimm CSR read/write immediate            (imm=CSR number) rd = csr,csr  = ZeroExt(uimm)
1110011 (115) 110 Icsrrsi rd,csr,uimm CSR read/set immediate                (imm=CSR number) rd = csr,
csr = csr |   ZeroExt(uimm)
1110011 (115) 111 Icsrrci rd,csr,uimm CSR read/clear immediate             (imm=CSR number) rd = csr, 
csr = csr & ~ZeroExt(uimm)Table B.8 Privileged / CSR instructions* If bit 11 of the immediate / offset / symbol is 1, the upper immediate is incremented by 1. symbol  and offset  are the 32-bit PC-relative addresses of a label 
  and a global variable, respectively.
For privileged / CSR instructions,  the 5-bit unsigned immediate, uimm, is encoded in the rs1 field.

