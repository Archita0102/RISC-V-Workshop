![image](https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/bdc41138-aa40-4b7d-bd46-9db5485d8cfd)# RISCV-ISA




## Table of Contents
- [Day 1 - Introduction to RISC V ISA and GNU compiler toolchain](#day-1---introduction-to-risc-v-isa-and-gnu-compiler-toolchain)
    * [Introduction](#introduction)
    * [Lab1 - Labwork for RISC-V Software toolchain](#lab1---labwork-for-risc--v-software-toolchain)
        + [1.Program to compute sum from 1 to N](#1-.-program-to-compute-sum-from-1-to-n)
        + [2.RISC-V GCC Compile and Disassemble](#2-.-risc-v-gcc-compile-and-disassemble)
        + [3.Spike Simulation and Debug](#3-.-spike-simulation-and-debug)
        + [4.Lab for Signed and unsigned integers](#4-.-lab-for-signed-and-unsigned-integers)
- [Day 2 - Introduction to ABI and basic verification flow](#day-2---introduction-to-abi-and-basic-verification-flow)
    * [Introduction to ABI and basic verification flow](#introduction-to-abi-and-basic-verification-flow)
    * [Load , Add and Store Instructions](#load-,-add-and-store-instructions)
    * [Lab1 - Labwork using ABI function calls](#lab1---labwork-using-abi-function-calls)
        + [1.New Algorithm for Sum 1 to N using ASM and Simulate](#1-.-new-algorithm-for-sum-1-to-n-using-asm-and-simulate)
    * [Lab2 - Basic verification flow using iverilog](#lab2---basic-verification-flow-using-iverilog)
        + [1.Lab to run C program](#1-.-lab-to-run-c-program)
-  [Day 3 - Digtial logic using TL Verilog and Makerchip](#day-3---digtial-logic-using-tl-verilog-and-makerchip)
    * [Labs for Combinational Logic](#labs-for-combinational-logic)
        + [1.New Algorithm for Sum 1 to N using ASM and Simulate](#1-.-new-algorithm-for-sum-1-to-n-using-asm-and-simulate)
        + [2.Arithmetic operators operate on binary numbers](#2-.-arithmetic-operators-operate-on-binary-numbers)
        + [3.Combinational Calculator](#3-.-combinational-calculator)
    * [Labs for Sequential Logic](#labs-for-sequential-logic)
        + [1.Fibonnaci Series](#1-.-fibonnaci-series)
        + [2.Sequential Calculator](#2-.-sequential-calculator)
    * [Labs for Pipelined Logic](#labs-for-pipelined-logic)
        + [1.Pythagoras with pipelined logic](#1-.-pythagoras-with-pipelined-logic)
        + [2.Calculator with piplelined logic](#2-.-calculator-with-piplelined-logic)
        + [3.Cycle Calculator](#3-.-cycle-calculator)


      



    

## Day 1 - Introduction to RISC V ISA and GNU compiler toolchain

### Introduction
- To make a C program run on a hardware it should be first compiled first into an assembly language program . In this case it is RISC-V architecture. Later it is connected into binary language program which is understood by the CPU.
- RTL implements the specification of assembly language.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/3694c5a0-bfa1-4d86-9ee5-6397bee850b1"> 

- System software converts the application program into a binary language. Major components of system software are OS , compiler and assembler.
- OS converts the app into its respective assembly language and finally into binary language program. C language are converted into instructions belonging to the specific hardware.
- Assembler converts the instructions into binary language.
- Binary language is further fed into hardware and the hardware performs accordingly.
- Instruction set architecture is the language spoken with the computer. Its an abstract interface between the user and the hardware.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/91c89cad-72dc-46df-b1c3-cbae29c6c016"> 

- ***Psuedo Instructions***: Instructions those are related to the positioning of the program. Eg. mov,li.
- ***Base Integer Instructions***: Insturctions opearting on integer numbers.The nomenclature to represent these instructions is RV64I. (64-bit data). Eg. addi.
- ***Multiply Extension***: If apart from RV64I hardware implements some multiplication instructions they are categorized here. Nomenclature is RV32M. Eg. mulw,divw.
- ***Single and Double precision floating point extension***: Instruction dealing with floating point numbers. Nomenclature is RV64F and RV64D. Eg. flw,fsd where f stands for floating point.
- ***Application binary interface(ABI)***: Keywords/Interface of the system available for the programmers where registers can be accessed directly.
- ***Memory allocation and stack pointer***: Data transfer instructions from register and the memory.

### Lab1 - Labwork for RISC-V Software toolchain

#### 1.Program to compute sum from 1 to N

Lets write a simple C program to compute sum from 1 to N in leafpad editor.

 <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/4d53cc67-3d05-4c36-b189-f86eddeb40b4"> 

Following is the output of the program
 <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/d97e4dbe-cc24-477d-838f-a8d1d9731f2a"> 


 #### 2.RISC-V GCC Compile and Disassemble

 - Compiling the program using a RISC-V compiler. The compiling commands are used. An object file is created

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/7b9e308b-1b4a-4567-8fe1-7d971056ee07"> 

 - To see the assembly language of the above C program. the below command gives a bunch of assembly language code.
 - Search for the main function (```/main``` and press n to enter to find next).

```
riscv64-unknown-elf-objdump -d sum1ton.o
riscv64-unknown-elf-objdump -d sum1ton.o | less
```
- Following is the assembly language program and the total number of instructions in main function.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/7b464569-eb2b-4b8e-92fb-8d0f15c6da22"> 

```
q: used to quit from a running program
```
- Now the the Ofast command.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/b7010058-3a5f-4508-a996-99f86553b475"> 
  
- Follwoing assembly language code is obtained.
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/523905c7-d60b-41ed-ae21-f208c568e6ce"> 

```
___
Explanation of the commands :

riscv64-unknown-elf-gcc - RISC-V  compiler

O1/Ofast -

mabi=lp64 - lp( long integer pointer )

march=rv64i - Architecture of RISC-V

sum1ton - output object file

objdump -

d: disassemble -

___

```

#### 3.Spike Simulation and Debug

- The output we obtained from C program should be the same we achieve using riscv compiler.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/d82bf2ab-a5e6-403a-b698-3e3333046050"> 

- Debugging the code. Type the following command
```
spike -d pk sum1ton.o
```
- To find contents of a particular register.
```
reg 0 a2
```
- Press enter to load the next instruction.
***lui: Load upper immediate. Bits from 12 to 31 will only be changed***
***addi: Add immediate. Add contents of source into destination register***

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/e4a7cb2b-467a-47d8-92a4-940fe5b1e5d9"> 

___
```

Explanation of the commands :

spike-

pk-

until- to make a program run till certain address

```
___

#### 4.Lab for Signed and unsigned integers

- The entire 64 bit number is called as the doubleword. 32 bit is called word.
- Total number of patterns generated by RV64 are 0 to (2^(64)-1). (unsigned) and for -(2^(64)-1) to +(2^(64)-1)(signed).
- For negative numbers 2's complement is used. MSB -1 : Negative number 0- Positive Number


- Create a simple unsigned integer program to find the highest number in unsigned long long int.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/36cfbf92-7e5d-4227-b09a-079cedcd7bbd"> 

- Following output we obtain using riscv compiler
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/b99bc8b8-fc3b-4cc1-ae8f-a98ebeed8196"> 
      
- Even if we increase the power from 64 to a higher number which is out of the limits of unsigned long long int , we will still obtain the answer for 2^64.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/eb9dd306-51bb-490d-adf1-ffcf55752b06"> 

- If within limits we obtain the correct maxminum number.

  <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/a296c822-581a-4fae-aa84-b1d959dbfabc"> 

- Unsigned integers dont cross 0 as the range starts from 0 to the max number.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/7ebd4158-b277-46a0-9eff-e59e0f481fbe"> 


- Create a simple signed integer program to find the highest number in unsigned long long int.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/47667f1b-c120-4ec6-abe6-2e430a2aaf51"> 

- Here we can obtain the highest integer of an signed number. But the output we obtain is incorrect.

  
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/98644176-a9a0-41a7-9f65-3c23f90b159d"> 

- The bug is maximum value of int variable is -2147483647 to 2147483648
- Hence , we have to specify long long int to extend the value of the answer.

 <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/e2db463f-79ec-4752-bc0b-97c589e25a7d"> 



## Day 2 - Introduction to ABI and basic verification flow

### Introduction to ABI and basic verification flow

- Application program uses standard libraries for different programming language we willuse.
- ISA is an interface between the OS and machine langugae (bit language). RTL helps in implementing the specifications defined by ISA on hardware.
- ISA is visible to both OS and to programmer called as User and System ISA.
- Application program can access some of the hardware of the OS directly through system calls. The application porgram can directly access the registers through these system calls. This calling interface is called as application binary interface.


 <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/16d9df19-0b8a-4711-879e-93a91f55f2f9"> 

- ABI to access the hardware of the system it has to do it through registers.
- RISCV offers 32 registers. width of the registers can be 32/64 depending on the architecture we are using.
- RISC-V belongs to little endian memory addressing system where the data is stored in bytes starting from LSB to MSB.

### Load , Add and Store Instructions

- ``` ld : l stands for load and d for doubleword``` : ***ld destination , offset (source).***
- 
- Instruction size is 32 bits for both rv64 and rv32.
- opcode instructs the computer to load the double word command.
- rs1 is source register(5 bits). In this example it is 23.
- rd is the  destination register(5 bit). Example here 8 will be represented as 01000.
- offset will be represented in next 12 bits of immediate from 20 to 31.
- 
- ``` add : add two registers``` : ***add destination,source1,source2***
- ``` sd : store double. Store the data into memory``` : ***sd data register,offset(source register)***

   <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/49ec20f2-3c5b-4dbb-9245-3e6f8c116d89"> 

___
```
  R-type Instructions: Instructions that operate only on regiters.
  I-Type Instructions: Instructions that operate on regiters and an immediate value.
  S-Type Instructions: Instructions that operate on source registers only and an immediate value.
  ``` 
___

- Regsiters used are always 5 bit. Total number of register (2^5=32). hence we have 32 bit registers in RISCV architecture.
- Every register is given an ABI name so we can access the internal registers of riscv.
_

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/5c773f86-7495-4223-83a0-25d008ccac47"> 



###  Lab1 - Labwork using ABI function calls

#### 1.New Algorithm for Sum 1 to N using ASM and Simulate

- Writing code ina assemblr language program to compute sum of numbers from 1 to n.
- Arguments are passed through a0,a1 and returened through a0.
- Run the loop till we get to the end of execution.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/025cc00c-4d8a-4920-b50e-1494f26db8ea"> 



- Write a C program for sum of 1 to N. Here we have taken N=9.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/4d7d38d1-b795-43cd-9b4d-24f07e3c1d94"> 

- Create assembly language program of the above c using following commands.

```
leafpad load.S &
```
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/64c8f84f-552f-4e08-8645-c23dc6ab40cb">


- Running both the programs

  <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/ec902000-f4c6-48aa-9959-b1be4a0fec8a">

- Main program

 <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/c2c4dac3-dadf-473d-9c7e-75ebff6377ba">


### Lab2 - Basic verification flow using iverilog

#### 1.Lab to run C program

- Load the hex file of the C program in the memory. Read the memory through the CPU and the CPU will process the contents of the memory and display the output.

- To run the program on RISC-V CPU

In the labs section. There is picorv32.v RISC-V CPU. Entire verilog netlist is shown here and also its testbench

 <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/900ff375-fe10-4848-92c0-6d906e9d8be2">
	  <p align="center"> 
	<img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/24634a34-17b2-45a5-970f-df7325e28dab">


- Creating hex files. ``` rv321m.sh ``` file consists of set of scripts needed to convert into hex file and load into picorv32 memory.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/74a7cf8a-270d-4807-8f89-36ab36b0a7a6">

- At the end there are two hex files created.
```
firmware.hex
```

- To run the file for conversion into hex. Type the following command

```
chmod 777 rv32im.sh
./rv321m.sh
```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/96d0915f-6e78-4ae8-ad28-adce31cbc106">
	
- This creates a hex file.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/a9e048a6-1cc7-4019-a0ba-2b55fda05f1b">

- The application pattern gets converted into bit stream and this bit stream gets loaded into the firmware.

- The bit stream file looks like below image

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/ba18332f-f06a-4873-9265-9c54bb2cce9b">

- This bitstream gets loaded into the memory through the testbench.

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/7335b656-825a-4075-9250-0702a063cdca">
 

## Day 3 - Digtial logic using TL Verilog and Makerchip

### Labs for Combinational Logic

Introduction to the platform
- Go to makerchip IDE. Inside the Tutorials validity select Pythagorean example

#### 1.Logic gates


```
$inv = !$in;               // OR gate
$out_g = $in1 && $in2;   // AND gate
$or_g = $in1 || $in2;    // OR gate
$exor_g = $in1 ^ $in2;    // XOR gate
```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/e7316b09-7a10-4be0-9f5b-e648bce03110">

[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0mwh3m)


#### 2.Arithmetic operators operate on binary numbers

```
$out[4:0] = $in1[3:0] + $in2[3:0];

```
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/41675757-a8ef-4544-bb9d-17479d97be94">
  
[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0nZh2k)



#### 3.Combinational Calculator

```
$val1 = $rand4[3:0];
$val2 = $rand4[3:0];
$op[1:0] = $rand2[1:0];

$sum[31:0] =  $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$quot[31:0] = $val1 / $val2;

$out[31:0] = $op == 2'b00 ? $sum : ($op == 2'b01 ? $diff : ($op == 2'b10 ? $prod : ($op == 2'b11 ? $quot : (32'b0))));
```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/eb6c0e53-cb8d-4603-9023-a1dba2132502">
  
[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0pghWZ)
   


### Labs for Sequential Logic

#### 1.Fibonnaci Series

```
$num[31:0] = $reset ? 1 : (>>1$num + >>2$num);
```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/83d769c4-fcd6-4d34-81b3-a560b3111885">
  
[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0qjh3Y)
 


#### 2.Sequential Calculator
   
   <p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/44579eec-8e9e-4433-91ca-535f5316a4bc">
  
```
$val1 = >>1$out[31:0];
$val2 = $rand4[3:0];
$op[1:0] = $rand2[1:0];

$sum[31:0] =  $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$quot[31:0] = $val1 / $val2;

$out[31:0] = $reset ? 0 : ($op == 2'b00 ? $sum : ($op == 2'b01 ? $diff : ($op == 2'b10 ? $prod : ($op == 2'b11 ? $quot : (32'b0)))));

```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/c010f4e4-169e-43a8-9be2-2daf4642208d">

[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0vgh5J)
 

 

### Labs for Pipelined Logic
#### 1.Pythagoras with pipelined logic
   
```
|calc
      ?$valid
         @1
            $aa_sq[7:0] = $aa[3:0] ** 2;
            $bb_sq[7:0] = $bb[3:0] ** 2;
         @2
            $cc_sq[8:0] = $aa_sq + $bb_sq;
         @3
            $out[4:0] = sqrt($cc_sq);
```


<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/8e88abe0-267c-4af4-b6c8-43eec227ac21">

[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0wjhmJ#)


#### 2.Calculator with piplelined logic

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/bc2d27b8-d46f-4dd9-8280-ec16aede6026">


```
 $reset = *reset;
   $val2 = $rand4[3:0];
   $op[1:0] = $rand2[1:0];
   |calc
      @1
         $reset = *reset;
         $val1 = >>1$out[31:0];
         $cnt = $reset ? 0 : (>>1$cnt + 1); 
         
         $sum[31:0] =  $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $quot[31:0] = $val1 / $val2;
   
         $out[31:0] = $reset ? 0 : ($op == 2'b00 ? $sum : ($op == 2'b01 ? $diff : ($op == 2'b10 ? $prod : ($op == 2'b11 ? $quot : (32'b0)))));
```




<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/4a1cdca2-08e1-459f-8cc9-6231281b4c05">

[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0y8hwV#)


#### 3.Cycle Calculator

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/42700e71-b7fc-4372-b45c-04f8445549f4">

```
$reset = *reset;
   $val2 = $rand4[3:0];
   $op[1:0] = $rand2[1:0];
   |calc
      @1
         $reset = *reset;
         $val1 = >>2$out[31:0];
         $valid = $reset ? 0 : (>>1$valid + 1); 
         
         $sum[31:0] =  $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $quot[31:0] = $val1 / $val2;
   
         $out[31:0] = ($reset | !$valid) ? 0 : ($op == 2'b00 ? $sum : ($op == 2'b01 ? $diff : ($op == 2'b10 ? $prod : ($op == 2'b11 ? $quot : (32'b0)))));
   
```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/f6a13222-3cd5-4187-9b70-e28f871d1e60">

[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0zmhZo)



### Validity


#### 1.Pythagoras Example

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/f6a13222-3cd5-4187-9b70-e28f871d1e60">
[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0JZhvO)


#### 2.Compute Total Distance

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/a0544623-a9aa-4bc2-8e68-4495676914ca">

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/71f81d11-38df-4210-8b29-fd32cfe8f3b8a">

```
|calc
      @1
         $reset = *reset;
      ?$valid
         @1
            $aa_sq[31:0] = $aa[3:0] * $aa;
            $bb_sq[31:0] = $bb[3:0] * $bb;
         @2
            $cc_sq[31:0] = $aa_sq + $bb_sq;
         @3
            $cc[31:0] = sqrt($cc_sq);
      @4
         $tot_dist[63:0] = $reset ? 64'b0 : ($valid ?
                (>>1$tot_dist + $cc) : $RETAIN);  
                      //$RETAIN = >>$tot_dist
```


<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/cd7ef3b3-ef75-4ffd-9977-e5ab0fb4b6fe">

[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0KOhNG)


#### 3.Calculator with validity

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/07269879-a4f2-4a1e-934a-dc1f7d820250">

```
|calc
      @1
         $reset = *reset;
         $val1 = >>2$out[31:0];
         $valid = $reset ? 0 : (>>1$valid + 1); 
         $valid_or_reset = $reset | $valid ;
      ?$vaild_or_reset   
         
         @1
            $sum[31:0] =  $val1 + $val2;
            $diff[31:0] = $val1 - $val2;
            $prod[31:0] = $val1 * $val2;
            $quot[31:0] = $val1 / $val2;
         @2
            $out[31:0] = $reset  ? 0 : ($op == 2'b00 ? $sum : ($op == 2'b01 ? $diff : ($op == 2'b10 ? $prod : ($op == 2'b11 ? $quot : (32'b0)))));
```


<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/123d486e-f147-4210-90b8-472d8445415e">


[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0Mjh1K)



#### 4.Calculator Single Value Memory lab

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/0ea3e39a-168a-4ff3-b0f2-00bc0c117f56">

```
|calc
      @1
         $reset = *reset;
         $val1 [31:0] = >>2$out;
         $val2 [31:0] = $rand2[3:0];
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1 ;
         $valid_or_reset = $valid || $reset;

      ?$vaild_or_reset
         @1   
            $sum [31:0] = $val1 + $val2;
            $diff[31:0] = $val1 - $val2;
            $prod[31:0] = $val1 * $val2;
            $div[31:0] = $val1 / $val2;

         @2   
            $mem[31:0] = $reset ? 32'b0 :
                         ($op[2:0] == 3'b101) ? $val1 : >>2$mem ;

            $out [31:0] = $reset ? 32'b0 :
                          ($op[2:0] == 3'b000) ? $sum :
                          ($op[2:0] == 3'b001) ? $diff :
                          ($op[2:0] == 3'b010) ? $prod :
                          ($op[2:0] == 3'b011) ? $quot :
                          ($op[2:0] == 3'b100) ? >>2$mem : >>2$out ;
```


<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/a8c7e54c-0175-4ae1-8738-1c8b38e66e33">

[Code](https://www.makerchip.com/sandbox/0M8f5hkmk/0O7hj7)


      
## Day 4 - Digtial logic using TL Verilog and Makerchip

### Microarchitecture Of Single Cycle RISCV CPU


  ***RISC V BLOCK DIAGRAM***

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/2bd19a58-0f0d-4bf7-a2f4-d342c5b335f6">

- Program counter(PC) : Its is a pointer into the instruction memory that points the instruction to implement next.
- Instruction memory(IMem) : It sends the instruction to be implemented.
- Decode(Dec) : It decodes the instruction coming to it. The source and destination register , branch instructions ,etc.
- Adder : Computing next PC for the branch.
- Register File read (RF) : The source and destination registers are stored here.
- Arithmetic Logic Unit (ALU): To operate arithmetic operations.
- Data Memory (DMem):Store and Load instructions are instructed here.

Implementation plan
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/9893ff37-347c-4774-8d16-56cb96c4b60c">
- Load an initial template from 

[link](https://myth.makerchip.com/sandbox?code_url=https:%2F%2Fraw.githubusercontent.com%2Fstevehoover%2FRISC-V_MYTH_Workshop%2Fmaster%2Frisc-v_shell.tlv)



### Lab - Program Counter

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/0826c131-46b1-41fd-a7d5-8f4bfa05094f">

```
|cpu
      @0
         $reset = *reset;


      @0
         $pc[31:0] = >>1$reset ? 32'd0 : (>>1$pc+32'd4);
```

<p align="center"> 
      <img src=https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/c14ab893-2788-4a3f-88da-59c7ad6d5d64">

[code](https://myth.makerchip.com/sandbox/0L9fPhqvx/0r0hqR)

      

### Lab - Instruction fetch

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/71a9695e-b211-4126-9a84-044ad68242d4">
     
```
@0
         $reset = *reset;


      @0
         $pc[31:0] = >>1$reset ? 32'd0 : (>>1$pc+32'd4);
      @1
         $imem_rd_en = !$reset;
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         $instr[31:0] = $imem_rd_data[31:0];
      ?$imem_rd_en
         @1
            $imem_rd_data[31:0] = /imem[$imem_rd_addr]$instr;
            
```
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/c0e62647-2885-4a12-9a59-6bd82d737d6e">

[code](https://myth.makerchip.com/sandbox/0L9fPhqvx/0oYhnw#)


### Lab - Instruction decode

Step 1
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/1ab9e455-3b8e-4acf-bb04-b13410c6eea4">

Step 2
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/cd36e82c-04ec-4508-a30a-ebc93b177bd5">

Step 3
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/80a526b5-cf1e-46dc-85bf-97ecc269c2c9">

Step 4

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/d17bf67a-0053-4b78-9ed8-9c01859bdc0b">
	
```
   ///Instruction decode
      @1
         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] ==? 5'b11001 ||
                       $instr[6:2] ==? 5'b11100;
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
         
         $is_r_instr = $instr[6:2] ==? 5'b01011 ||
                       $instr[6:2] ==? 5'b011x0 ||
                       $instr[6:2] ==? 5'b10100;
         
         $is_b_instr = $instr[6:2] ==? 5'b11000;
         
         $is_j_instr = $instr[6:2] ==? 5'b11011;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
         
         $imm[31:0] = $is_i_instr ? {{21{$instr[31]}}, $instr[30:20]} :
                      $is_s_instr ? {{21{$instr[31]}}, $instr[30:25], $instr[11:7]} :
                      $is_b_instr ? {{20{$instr[31]}}, $instr[7], $instr[30:25], $instr[11:8], 1'b0} :
                      $is_u_instr ? {$instr[31:12], 12'b0} :
                      $is_j_instr ? {{12{$instr[31]}}, $instr[19:12], $instr[20], $instr[30:21], 1'b0} :
                                    32'b0;
         $opcode[6:0] = $instr[6:0];
         
         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr;
         ?$rs2_valid
            $rs2[4:0] = $instr[24:20];
            
         $rs1_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr;
         ?$rs1_valid
            $rs1[4:0] = $instr[19:15];
         
         $funct3_valid = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr;
         ?$funct3_valid
            $funct3[2:0] = $instr[14:12];
            
         $funct7_valid = $is_r_instr ;
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
            
         $rd_valid = $is_r_instr || $is_i_instr || $is_u_instr || $is_j_instr;
         ?$rd_valid
            $rd[4:0] = $instr[11:7];  
            
         $dec_bits [10:0] = {$funct7[5], $funct3, $opcode};
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_add = $dec_bits ==? 11'b0_000_0110011;  
         
      
         `BOGUS_USE($is_beq $is_bne $is_blt $is_bge $is_bltu $is_bgeu $is_addi $is_add)
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      //m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
      //m4+dmem(@4)    // Args: (read/write stage)
      //m4+myth_fpga(@0)  // Uncomment to run on fpga

   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule

```
<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/2c65b887-4b9f-4eeb-93cb-18d9fd1d92c2">

[code](https://myth.makerchip.com/sandbox/0L9fPhqvx/0xGhlk#)




### Lab - Register File Read

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/684f8c0a-c149-4069-9bd1-9149e5ea6120">


<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/e0c41a46-9e6a-449d-bb74-104232ac7669">

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/544c44a8-7b46-45a9-985b-b5a83c834bed">



```
/// Register file 
      @1
         $rf_wr_en = 1'b0;
         $rf_wr_index[4:0] = 5'b0;
         $rf_wr_data[31:0] = 32'b0;
         
         $rf_rd_en1 = $rs1_valid;
         $rf_rd_index1[4:0] = $rs1;
         
         $rf_rd_en2 = $rs2_valid;
         $rf_rd_index2[4:0] = $rs2;
         
         $src1_value[31:0] = $rf_rd_data1;
         $src2_value[31:0] = $rf_rd_data2;
```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/df04b0cd-0b71-4737-9c6b-56cda6101081">

[code](https://myth.makerchip.com/sandbox/0L9fPhqvx/0qjhQo)


### Lab - ALU

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/9c13f5cc-fe40-45b2-8344-e3cbe37c6979">

```
//ALU
      @1
         $result[31:0] = $is_addi ? $src1_value + $imm :
                         $is_add ? $src1_value + $src2_value :
                         32'bx ;
```


<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/589cecbf-6d4a-4a5f-b289-71af40999e30">
 

[code](https://myth.makerchip.com/sandbox/0L9fPhqvx/0DRhpo)


### Register File Write

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/569a5650-1257-4c68-aeaa-3e9624536443">


```
//Register File Write
      @1
         $rf_wr_en = $rd_valid && $rd != 5'b0;
         $rf_wr_index[4:0] = $rd;
         $rf_wr_data[31:0] = $result;
```

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/44b8d063-810e-4588-95cc-05ef963083a1">

[code](https://myth.makerchip.com/sandbox/0L9fPhqvx/0DRhpo)


### Branch Instructions

<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/582a46af-c457-4ea2-b5c9-f43d218c5ef9">

```
// Branch instruction
       @1
  
         $taken_branch = $is_beq ? ($src1_value == $src2_value):
                         $is_bne ? ($src1_value != $src2_value):
                         $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])):
                         $is_bge ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])):
                         $is_bltu ? ($src1_value < $src2_value):
                         $is_bgeu ? ($src1_value >= $src2_value):
                                    1'b0;
	$br_tgt_pc[31:0] = $pc + $imm;
```


<p align="center"> 
      <img src="https://github.com/Archita0102/RISC-V-Workshop/assets/66164675/9576262a-8215-4aaf-bad6-5e5cd0224953">


[code](https://myth.makerchip.com/sandbox/0L9fPhqvx/0Lghqm#)




### Branch Instructions








[Acknowledgement Section]:#
## Acknowledgement
1.  Kunal Ghosh, VSD Corp. Pvt. Ltd.
2.  Sumanto Kar, Sr. Project Technical Assistant , IIT Bombay
3.  Alwin Shaju, Colleague IIITB
4.  Adam Teman, Associate Professor at Bar-Ilan University in Ramat Gan, Israel  
5.  Pruthvi Parate, Colleague IIITB
6.  Emil Jayanth Lal, Colleague IIITB
7.  Bhargav D V, Colleague IIITB 
8.  Geetima Kachari, Assistant Professor NITS Mirza under Nemcare group of institutions
9.  Shivani Shah, Hardware Architect
10. Bala Dhinesh, Engineer Tenstorrent
11. Steve Hoover, Founder of Redwood EDA, LLC


[Reference Section]:#
## References
1. https://www.eng.biu.ac.il/temanad/digital-vlsi-design/
2. https://www.arm.com/glossary/isa
3. https://riscv.org/wp-content/uploads/2017/05/riscv-spec-v2.2.pdf
4. https://gcc.gnu.org/onlinedocs/gcc/RISC-V-Options.html
5. https://www.tutorialspoint.com/unsigned-and-signed-binary-numbers
6. https://book.rvemu.app/instruction-set/01-rv64i.html
7. https://github.com/shivanishah269/risc-v-core
8. https://github.com/RISCV-MYTH-WORKSHOP/RISC-V-CPU-Core-using-TL-Verilog
9. https://github.com/stevehoover/RISC-V_MYTH_Workshop
