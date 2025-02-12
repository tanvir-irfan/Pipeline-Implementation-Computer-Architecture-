Project Description:

Code starts at address 0.
Each instruction is 4 byte
Data starts at address 1024*1024
Data is laid out in little endian form
Only integer register
All operations are on integer
32 bit registers
R0 always 0

Output:
Contents of each register, in sorted order
Contents of each address accessed in the program, in sorted order

Simulate whole program or first 1000 clock cycles whichever happens first

You have to implement a classic 5 stage MIPS pipeline. It has the following stages:
    IF, ID, EXE, MEM, WB
 The stages are the same as the one we studied in the class. 
 The pipeline should have the following properties:
 - Each register and each instruction is 32 bits long.
 - No forwarding or bypassing is used in the pipeline.
 - A register written in the first half of a clock cycle and read in the second half.
 - Branch is resolved (condition evaluation and target calculation) in EXE stage. So, you can
   fetch new instruction from the target when the branch instruction is in MEM stage.
 - Separate code and data memory are used. Assume that each memory is 1024 bytes long. Code
   starts at address 0 and data can reside at any address in data memory.
 - For simplification, assume that each load or store operation accesses 32 bit (4 byte)
   of memory.
 - All arithmetic operations are interger operations.
 - The pipeline has 8 registers: R0, R1, R2, ... R6, and R7. R0 always holds 0.
 - The pipeline should support the following MIPS instructions:
      NOP       [Example: NOP                  :  Do nothing]
      ADD       [Example: ADD R1 R2 R3         :  R1 = R2 + R3]
      SUB       [Example: SUB R1 R2 R3         :  R1 = R2 - R3]
      MUL       [Example: MUL R1 R2 R3         :  R1 = R2 * R3]
      DIV       [Example: DIV R1 R2 R3         :  R1 = R2 / R3]
      XOR       [Example: XOR R1 R2 R3         :  R1 = R2 ^ R3]
      AND       [Example: ADD R1 R2 R3         :  R1 = R2 & R3]
      OR        [Example: OR R1 R2 R3          :  R1 = R2 | R3]
      ADDI      [Example: ADDI R1 R2 100       :  R1 = R2 + 100]
      SUBI      [Example: ADDI R1 R2 100       :  R1 = R2 - 100]
      LD        [Example: LD R1 R2 32          :  R1 = DataMem[R2 + 32]]
      ST        [Example: ST R1 R2 32          :  DataMem[R2 + 32] = R1]
      BEQZ      [Example: BEQZ R1 100          :  if R1==0 goto instruction at address PC_of_Branch + 4 + 100 * 4]
      BNEQZ     [Example: BNEQZ R1 100         :  if R1!=0 goto instruction at address PC_of_Branch + 4 + 100 * 4]
      HLT       [Example: HLT                  :  Terminate program]
 - Your program (say, its name is "pipeline") should take one command line parameter. Example:
    ./pipeline program_num
    where program_num indicates one of the programs embedded in the pipeline.cpp file. Any value
    from 1 to 6 will load that program into instruction memory and print the output.
 - Your program should start fetching instructions from instruction memory
   at address 0. 
 - You should simulate the MIPS program upto 1000 cycles or until an "HLT" instruction is finished 
   (whichever happens first).
 - The program writes the following quantities:
    [Your Name], [Your abc123 id]
    [total instructions fetched]
    [total instructions finished]
    [total cycles]
    [total stall cycles]
    [R1]
    [R2]
    [R3]
    [R4]
    [R5]
    [R6]
    [R7]
