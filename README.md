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


   






