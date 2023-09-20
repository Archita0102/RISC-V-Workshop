# RISC-V-Workshop
The repository is a detailed description of the RISC-V Workshop organised by VSD team. The labwork is a complete handon performed by Archita Malgaonkar


##LAB-1: Labwork for RISC-V software toolchain

###C Program to compute Sum from 1 to N

Editor used - leafpad
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/de9f8616-1f3a-4d47-ae6a-df781cdba6ed)

![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/9622b457-006d-429e-b3b6-5347184f6567)

![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/5f19bc0a-f79f-4913-a424-a5af28beff8c)


###RISCV GCC compile and Disassemble

Compiling with RISCV GCC compiler. Generates an output file with extension .o
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/d2794b3f-c927-4dfd-b8e3-2d9bc877bcc9)

Assembly code for the program
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/25c57dce-f4d7-42ec-bf4d-6268d79838b6)


![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/f680655d-6934-47f5-86e9-a7d2ae7df7f7)

The following program is a huge section of the code.
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/6ad6e5d8-3fcb-4a4d-8d4f-224c67e5d766)

Search for the main program
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/8edc2914-b685-48e0-952b-a9eaab5b1c05)

Address of main is 000000000010184 and it is byte addressable. Main has 11 instructions.

Running Ofast instead of O1
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/1394c2f6-14bc-43f9-a957-55f77f72dfce)

Again the main function and count the number of instructions.
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/5adea9a1-dc2e-4fb2-8e6f-6f850803aa44)



###Spike Simulation and Debug

The output that we obtain using .c file should match with the riscv compiler.
The command used for that is spike pk

![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/2d9d0a00-60b6-4938-ab3f-5db69f59694a)

Debugging the above code.

lui(Load Upper Immediate): Load the upper immediate of the second operand in the first.
addi(Add immediate): Add source and destination and enter the data in destination.
![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/330c6691-8722-4d44-b060-6f262282dc9d)


