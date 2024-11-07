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























   
​



   
   
   


 





   






