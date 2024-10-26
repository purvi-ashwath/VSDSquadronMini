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





   
​



   
   
   


 





   






