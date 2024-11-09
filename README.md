# VSDSquadronMini Research Internship - 20th October Cohert 
## Lab exercises of RISCV workshop 
Instructor: Kunal Ghosh

## Task1: Install RISC-V toolchain using VDI.Upload snapshot of compiled C code and RISC-V Objdmp on your GitHub repo
### DESCRIPTION:
> The task included downloading a virtual manager and installing the RIS-V toolchain using VDI
> Write a C code for the sum to n numbers
> Compile the above code using gcc compiler
> Compile the above code using the RISC-V simulator

### INSTALLATIONS:
> Oracle Virtual machine
![Screenshot 2024-10-22 152031](https://github.com/user-attachments/assets/8c5c050f-21e4-45b3-9bf9-46a04526adc7)


> Leafpad editor
![terminal](https://github.com/user-attachments/assets/ff1769fa-d7c7-44fd-bb57-85b5ef917316)

### STEPS:
1. Open leafpad and write the C code to find the sum of n numbers
   ![sumofnumbers_c_code](https://github.com/user-attachments/assets/914f2e6e-4bcb-4fd2-9a68-2ec1b3745517)
2. Compile the above code using gcc and get the output
   ![sum_of_numbers_output](https://github.com/user-attachments/assets/2bcccdeb-114a-4bca-9078-408fc8ad7b21)
3. Now, compile and run the same code using the RISC-V Simulator
   ![main_15_instructions](https://github.com/user-attachments/assets/8d859bed-4fd8-4ef5-8f79-7920ae83da43)
Search for main usin the commands:
"riscv64-unknown-elf-objdump -d sum.o | less" and then type out "/main"
4. Changing it from O1 to Ofast:
    ![main_Ofast](https://github.com/user-attachments/assets/18eb6fb2-cae2-4cd7-83ca-23fa218614db)


## TASK 2:
## A. SPIKE Simulation and observation with -O1 and -Ofast.  Upload snapshot of compiled C Code, RISC-V Objdmp 
# STEPS:
1. The C Code is the same above:
 ![sumofnumbers_c_code](https://github.com/user-attachments/assets/914f2e6e-4bcb-4fd2-9a68-2ec1b3745517)
2. Ofast: output using risv simulator
   ![main_Ofast](https://github.com/user-attachments/assets/18eb6fb2-cae2-4cd7-83ca-23fa218614db)
3. Now, confirm the same using spike and the below screenshot also involves debugging
   ![spike](https://github.com/user-attachments/assets/d1de6bfa-20f3-48ae-8569-336c6329e726)
This confirms that all the three methods give the same output.


## B. Write a simple C program for any  simple application and RISC-V GCC/SPIKE
## STEPS:
1. Choose an application. I chose a digital design application- Carry Look Ahead Adder(CLA)
### CLA:
A Carry Look-Ahead Adder (CLA) is a type of digital adder used in computer arithmetic to speed up the addition process by reducing the time taken to calculate carry bits. Unlike a simple ripple-carry adder, which propagates carry bits sequentially through each bit position, a CLA adder generates carry signals in parallel, based on input bits and previous carry bits. This leads to faster computations, especially for adders with a large number of bits.
### Working Principle
The CLA adder uses two key concepts:
#### Generate (G): A bit position generates a carry if both bits being added (A and B) are 1, regardless of any carry-in.

𝐺𝑖=𝐴𝑖⋅𝐵𝑖

#### Propagate (P): A bit position propagates a carry if either A or B is 1, meaning any incoming carry will pass through to the next bit.

Pi=Ai+Bi

The carry-out for each bit can then be expressed using these generate and propagate values without having to wait for each preceding bit’s carry-out.

For a 4-bit adder, the carry-out values for each position (C1, C2, C3, etc.) can be determined as:

C1=G0+P0.C0

C2=G1+P1.C1

C3=G2+P2.C2

C4=G3+P3.C3

CLA adders are widely used in high-speed arithmetic circuits within processors, ALUs (Arithmetic Logic Units), and other hardware that requires rapid computation.

2. Write the C Code for CLA using the above given logic
   ![cla c code](https://github.com/user-attachments/assets/0ca1767e-6a70-4406-8b72-4b8f27cfaddf)
3. First,compile it using gcc
   ![cla gcc (take 2 ss)](https://github.com/user-attachments/assets/41f8dc9b-1f6e-4c4b-b7d2-77b348a89479)
4. Secondly, compile the same C Code using the RISV simulator. The code for that is present in the above image too. The output is:
   ![cla risv ](https://github.com/user-attachments/assets/d843d654-0086-4c8c-b563-66b2766d379e)
5. Finally, compile the program using SPIKE simulator
   ![cla spike](https://github.com/user-attachments/assets/160cc7c2-23e4-4a81-a258-0fd2137a7465)


From the above observation it is clear that all three compilers/simulators produce the same output for the C Code.

### TASK 3
## A. List various RISC-V instruction type (R, I, S, B, U, J) after going through RISC-V software documentation.
# What is RISC-V?
(i)  RISC-V is an open-source instruction set architecture (ISA) that allows developers to develop processors for specific applications.
(ii) RISC-V is based on reduced instruction set computer principles and is the fifth generation of processors built on this concept.

# INSTRUCTIONS FORMAT IN RISC-V
The instruction format of a processor refers to how machine language instructions are structured and organized for execution by the processor. These instructions are composed of sequences of 0s and 1s, each encoding information about the data's location and the operations to be performed.

There are 6 instruction formats in RISC-V:
1. R-format
2. I-format
3. S-format
4. B-format
5. U-format
6. J-format

![image](https://github.com/user-attachments/assets/186ae499-fe22-4dcf-855c-ab244c572304)
1. "opcode" represents a 7-bit instruction operator code, its role is to distinguish between different instructions.
2. "funct3" represents a 3-bit function code.it is an additional opcode.
3. "funct7" represents a 7-bit function code, which can help distinguish different kinds of instructions.
4. "rs1" and "rs2" represent two 5-bit source registers.
5. "rd" is a 5-bit destination register, and the result of the instruction operation is stored in rd.
6. "imm" represents an immediate number of different lengths, which can be used directly as an operand.

# 1. R-type Instruction (Register-Type):
![image](https://github.com/user-attachments/assets/387e83a2-1e84-4468-878c-dba5df1c79b0)
funct7 (bits 31-25): Used to differentiate between similar instructions. Often used for encoding the operation, such as shift amount or sign extension.\
rs2 (bits 24-20): Source register 2.\
rs1 (bits 19-15): Source register 1.\
funct3 (bits 14-12): Specifies the operation to be performed (e.g., add, subtract, etc.).\
rd (bits 11-7): Destination register.\
opcode (bits 6-0): Specifies the type of instruction (e.g., arithmetic, logical).\
Operation: R-Type instructions perform register-to-register operations like arithmetic (ADD, SUB), logical (AND, OR), and shifts (SLL, SRL).

# 2. I-type Instruction (Immediate-Type):
![image](https://github.com/user-attachments/assets/f7a02162-9236-4ffd-a72b-9dbb340b2a93)
imm[11:0] (bits 31-20): Immediate value (12-bit signed) that is directly used as an operand.\
rs1 (bits 19-15): Source register.\
funct3 (bits 14-12): Specifies the operation (e.g., load, add immediate, etc.).\
rd (bits 11-7): Destination register.\
opcode (bits 6-0): Specifies the type of instruction.\
Usage: I-Type instructions are typically used for operations that involve an immediate value, such as ADDI (add immediate), load instructions (LW), and some system calls.

# 3. S-type Instruction (Store-Type):
![Screenshot 2024-11-07 214733](https://github.com/user-attachments/assets/11f2ca44-fef3-4f8c-9a7b-16a5ee5c6915)
imm[11:5] (bits 31-25): Upper 7 bits of the immediate value.\
rs2 (bits 24-20): Source register 2 (data to be stored).\
rs1 (bits 19-15): Source register 1 (base address).\
funct3 (bits 14-12): Specifies the operation (e.g., store byte, store word).\
imm[4:0] (bits 11-7): Lower 5 bits of the immediate value.\
opcode (bits 6-0): Specifies the type of instruction.\
Usage: S-Type instructions are used for store operations, where the value in rs2 is stored in memory at the address computed by adding the immediate value to rs1. Example: SW (store word).

# 4. B-Type Instruction (Branch-Type):
![Screenshot 2024-11-07 214740](https://github.com/user-attachments/assets/64e46d79-2783-4cb7-9e25-4239ede3e987)
imm[12] (bit 31): 12th bit of the immediate value.\
imm[10:5] (bits 30-25): Bits 10 through 5 of the immediate value.\
rs2 (bits 24-20): Source register 2 (used for comparison).\
rs1 (bits 19-15): Source register 1 (used for comparison).\
funct3 (bits 14-12): Specifies the condition for the branch (e.g., equal, less than).\
imm[4:1] (bits 11-8): Bits 4 through 1 of the immediate value.\
imm[11] (bit 7): 11th bit of the immediate value.\
opcode (bits 6-0): Specifies the type of instruction.\
Usage: B-Type instructions are used for conditional branching based on comparisons between rs1 and rs2. Examples include BEQ (branch if equal) and BNE (branch if not equal).

# 5. U-Type Instruction (Upper Immediate-Type):
![Screenshot 2024-11-07 214746](https://github.com/user-attachments/assets/267c799c-3dd1-47e8-862c-0859ca6e3d81)
imm[31:12] (bits 31-12): 20-bit immediate value.\
rd (bits 11-7): Destination register.\
opcode (bits 6-0): Specifies the type of instruction.\
Usage: U-Type instructions are used to load a 20-bit immediate value into the upper 20 bits of a register. Example: LUI (load upper immediate).

# 6. J-Type Instruction (Jump-Type):
![Screenshot 2024-11-07 214753](https://github.com/user-attachments/assets/bb4c4c3e-747a-4b6f-845e-05487e6c8bd7)
imm[20] (bit 31): 20th bit of the immediate value.\
imm[10:1] (bits 30-21): Bits 10 through 1 of the immediate value.\
imm[11] (bit 20): 11th bit of the immediate value.\
imm[19:12] (bits 19-12): Bits 19 through 12 of the immediate value.\
rd (bits 11-7): Destination register (used to store the return address).\
opcode (bits 6-0): Specifies the type of instruction.\
Usage: J-Type instructions are used for jump operations, such as JAL (jump and link), where the program jumps to a specific address and stores the return address in the destination register.

## B. Identify 15 unique RISC-V instructions from riscv-objdmp of your application code.Identify exact 32-bit instruction code in the instruction type format for 15 unique instructions.

 ![image](https://github.com/user-attachments/assets/b63a253c-bf67-41c0-9313-df34e362bfd9)
**1.lui a0, 0x2b**
Type: U-Type\
Opcode (LUI): 0110111 (7 bits)\
rd (a0): x10 = 01010 (5 bits)\
Immediate (0x2b): 00000000000000101011 (upper 20 bits)\
32-bit instruction: (00000000000000101011 01011 0110111)2\
**2. addi a0, a0, -544**
Type: I-Type\
Opcode (ADDI): 0010011 (7 bits)\
rd (a0): x10 = 01010 (5 bits)\
rs1 (a0): x10 = 01010 (5 bits)\
funct3: 000 (3 bits)\
Immediate (-544): 110111100000 (12 bits, two's complement for -544)\
32-bit instruction: (110111100000 01010 000 01010 0010011)2 \
**3. sd s3, 40(sp)**
Type: S-Type\
Opcode (SD): 0100011 (7 bits)\
rs1 (sp): x2 = 00010 (5 bits)\
rs2 (s3): x19 = 10011 (5 bits)\
funct3: 011 (3 bits)\
Immediate (40): 000000101000 (split into imm[11:5] and imm[4:0])\
imm[11:5]: 0000001\
imm[4:0]: 01000\
32-bit instruction: (0000001 10011 00010 011 01000 0100011)2\
**4. jal ra, 10634**
Type: J-Type\
Opcode (JAL): 1101111 (7 bits)\
rd (ra): x1 = 00001 (5 bits)\
Immediate (10634): 010101110000 (split into imm[20|10:1|11|19:12])\
imm[20] = 0\
imm[10:1] = 1010101110\
imm[11] = 0\
imm[19:12] = 00000000\
32-bit instruction: (0 1010101110 0 00000000 00001 1101111)2 \
**5. li s2, 5**
Type: I-Type\
Opcode (ADDI): 0010011 (7 bits)\
rd (s2): x18 = 10010 (5 bits)\
rs1 (x0): x0 = 00000 (5 bits)\
funct3: 000 (3 bits)\
Immediate (5): 000000000101 (12 bits)\
32-bit instruction: (000000000101 00000 000 10010 0010011)2\
**6. addiw s0, s0, 1**
Type: I-Type\
Opcode (ADDIW): 0011011 (7 bits)\
rd (s0): x8 = 01000 (5 bits)\
rs1 (s0): x8 = 01000 (5 bits)\
funct3: 000 (3 bits)\
Immediate (1): 000000000001 (12 bits)\
32-bit instruction: (000000000001 01000 000 01000 0011011)2\
**7. mv a1, s0**
Type: I-Type\
Opcode (ADDI): 0010011 (7 bits)\
rd (a1): x11 = 01011 (5 bits)\
rs1 (s0): x8 = 01000 (5 bits)\
funct3: 000 (3 bits)\
Immediate (0): 000000000000 (12 bits)\
32-bit instruction: (000000000000 01000 000 01011 0010011)2 \
**8. bne s0, s2, 100ec**
Type: B-Type\
Opcode (BNE): 1100011 (7 bits)\
rs1 (s0): x8 = 01000 (5 bits)\
rs2 (s2): x18 = 10010 (5 bits)\
funct3: 001 (3 bits)\
Immediate (100ec): 111111100100 (split into imm[12|10:5|4:1|11])\
imm[12] = 1\
imm[10:5] = 111111\
imm[4:1] = 0000\
imm[11] = 1\
32-bit instruction: (1 111111 10010 01000 001 0000 1 1100011)2\
**9. lw a4, 8(sp)**
Type: I-Type\
Opcode (LW): 0000011 (7 bits)\
rd (a4): x14 = 01110 (5 bits)\
rs1 (sp): x2 = 00010 (5 bits)\
funct3: 010 (3 bits)\
Immediate (8): 000000000100 (12 bits)\
32-bit instruction: (000000001000 00010 010 01110 0000011)2\
**10. blt a4, a2, 101dc**
Type: B-Type\
Opcode (BLT): 1100011 (7 bits)\
rs1 (a4): x14 = 01110 (5 bits)\
rs2 (a2): x12 = 01100 (5 bits)
funct3: 100 (3 bits)\
Immediate (101dc): 000110011000 (split into imm[12|10:5|4:1|11])\
imm[12] = 0\
imm[10:5] = 000110\
imm[4:1] = 0000\
imm[11] = 0\
32-bit instruction: (0 000110 01100 01110 100 0000 0 1100011)2\
**11. sext.w a5, a4**
Type: R-Type\
Opcode (SLLIW): 0011011 (7 bits)\
rd (a5): x15 = 01111 (5 bits)\
rs1 (a4): x14 = 01110 (5 bits)\
funct3: 000 (3 bits)\
rs2: 00000 (5 bits)\
funct7: 0000000 (7 bits)\
32-bit instruction: (0000000 00000 01110 000 01111 0011011)2\
**12. ld s0, 64(sp)**
Type: I-Type\
Opcode (LD): 0000011 (7 bits)\
rd (s0): x8 = 01000 (5 bits)\
rs1 (sp): x2 = 00010 (5 bits)\
funct3: 011 (3 bits)\
Immediate (64): 000000010000 (12 bits)\
32-bit instruction: (000001000000 00010 011 01000 0000011)2\
**13. j 10174**
Type: J-Type\
Opcode (JAL): 1101111 (7 bits)\
rd (x0): x0 = 00000 (5 bits)\
Immediate (10174): 111111110100 (split into imm[20|10:1|11|19:12])\
imm[20] = 1\
imm[10:1] = 1111100110\
imm[11] = 1\
imm[19:12] = 11111111\
32-bit instruction: (1 1111100110 1 11111111 00000 1101111)2 \
**14. ret**
Type: I-Type\
Opcode (JALR): 1100111 (7 bits)\
rd (x0): x0 = 00000 (5 bits)\
rs1 (ra): x1 = 00001 (5 bits)\
funct3: 000 (3 bits)\
Immediate (0): 000000000000 (12 bits)\
32-bit instruction: (000000000000 00001 000 00000 1100111)2\
**15. xor a8, a1, a4**
Type: R-Type\
Opcode (XOR): 0110011 (7 bits)\
rd (a8): x8 = 01000 (5 bits)\
rs1 (a1): x1 = 00001 (5 bits)\
rs2 (a4): x4 = 00100 (5 bits)\
funct3: 100 (3 bits)\
funct7: 0000000 (7 bits)\
32-bit instruction: (0000000 00100 00001 100 01000 0110011)2


## TASK 4: By making use of RISC-V Core: Verilog Netlist and Testbench, perform an experiment of Functional Simulation and observe the waveforms
NOTE: Since the designing of RISCV Architecture and writing it's testbench is not the part of this Research Internship, so we will use the Verilog Code and Testbench of RISCV that has already been designed. The reference GitHub repository is : iiitb_rv32i

### Steps to perform functional simulation of RISCV
1. Open your terminal and type the following to install iverilog and GTKWave
   $   sudo apt get update
   $   sudo apt get install iverilog gtkwave
2. Create a new directory with your name mkdir <your_name>
3. Create two files by using touch command as purvi_rv32i.v and purvi_rv32i_tb.v
4. Copy the code from the reference github repo and paste it in your verilog and testbench files
5. To run and simulate the verilog code, enter the following command:
   $ iverilog -o purvi_riscv purvi_rv32i.v purvi_rv32i_tb.v
   $ ./purvi_riscv
6. The above will result in a vcd file being formed and the name of the file will be listed in the comments
7. To see the simulation waveform in GTKWave, enter the following command
   $ gtkwave iiitb_rv32i.vcd
   ![terminalgtk](https://github.com/user-attachments/assets/fc5b8948-e7a2-425d-b84d-826085e30986)

9. The GTKWave will be opened.
10. Drag the required signals.
    ![signals](https://github.com/user-attachments/assets/fbc5122b-0851-44f9-8a13-c222f8b5344f)

11. Observe the waveform.

### Instruction 1 : ADD R6, R2, R1
![Screenshot 2024-11-08 221742](https://github.com/user-attachments/assets/099bf13e-7a12-4de9-be41-35ee28d91aa5)

### Instruction 2 : SUB R7, R1, R2
### Instruction 3 : AND R7, R1, R2
### Instruction 4 : OR R7, R1, R2
### Instruction 5 : XOR R7, R1, R2
### Instruction 6 : SLT R7, R1, R2
### Instruction 7 : ADDI R7, R1, R2
### Instruction 8 : BEQ R7, R1, R2

















   
​



   
   
   


 





   






