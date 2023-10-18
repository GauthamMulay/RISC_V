# gautham_RISCV
## RISC based MYTH
RISC based MYTH (microprocessor for you in thirty hours) is a workshop which helps us build a RISC-V processor in 5 days.This RISC-V processor is designed with the help of Transaction Level Verilog (TLVerilog) made use in MakerChip IDE platform.
In this workshop, we will be working from Day 3 onwards.
### DAY 3
#### Digital logic with TL-Verilog and Makerchip
#### Combinational logic in TL-Verilog and mackerchip
**Basic logic gates:**

 <img width="394" alt="image" src="https://github.com/GauthamMulay/RISC_V/assets/113660503/88559464-a01e-46b7-b5a7-918a1fa3c014">
 
The following are basic combinational logic in TL-Verilog:

1.Inverter:
  - Navigate under TLV Section and type:
        ```$out = ~ $in```
  - Compile by clicking on ``` E ``` on the top right corner
    
2.XOR gate:

  ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/031ca215-248d-4c0b-b6d9-84d0b679a1a5)

3.Vector:

  ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/c201c800-097b-41a3-9210-b2ebe83c5156)

4.MUX (With and without vector):

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/198a8782-1fcf-41ca-8c65-226fb32771c7)

5.Simple Calculator:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/dd6a50b0-a468-4d0b-a3b1-9d2f62ca2a72)

### Sequential Logic
The following are sequential logic coded in TL-Verilog:

1.Fibonacci Series:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/deaee09c-d307-432c-8719-1a83acf71cb8)

2.Calculator with Reset:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/e9e0a169-d35f-41c9-87c9-5fc0c133ff16)

3.Pipelining with pythogorus theorm example:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/c5f4a64b-3917-4cfd-b55f-1c61aaa04906)

### Validity
* Addding validity makes it easier to debug.
* It provides a cleaner design.
* Automatic clock gating.

1.Distance Calculator:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/20f22318-ccc5-4b11-8d32-42efbfc700b7)

2.2 cycle calculator with validity:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/13023f41-821b-455b-9e4f-c8de5f11997f)

  

## DAY 4
### Basic RISC-V CPU Micro Architecture
#### RISC-V Implementation
<img width="325" alt="image" src="https://github.com/GauthamMulay/RISC_V/assets/113660503/557382cd-9de9-4d8d-bf53-0ca05e8bfbf7">


**1.CPU:**
The CPU serves as the core of the RISC-V processor, responsible for executing instructions. It includes multiple stages:
- Instruction Fetch (IF): Fetches instructions from memory.
- Instruction Decode (ID): Decodes the fetched instructions.
- Execution (EX): Performs arithmetic and logic operations.
- Memory (MEM): Manages data memory access.
- Write Back (WB): Writes results back to registers.
  
**2.Program Counter:**
  - Program Counter is a register that contains the address of the next instruction to be executed.
  - For the initial state, before fetching the first ever instruction, there is a presence of a reset signal that will reset the PC value to 0.
  - For branch instructions, we will have immediate instructions, for which we have to add an offset value to the PC. So for branch instructions, ```NextPC = Incremented PC + Offset value```
    
   ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/0eb54e2c-bab2-4322-8468-e71e900c3043)

**3.Instruction Fetch:**
  - In the Instruction Fetch logic, the instructions are fetched from the instruction memory amd passed to the Decode logic for computation.
  - In our case, the Makerchip shell provides us an instantiation to the instruction memory, which contains a test program to compute the sum of numbers from 1 to 9.
    
    ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/6f664766-ffbe-4347-bf59-16ac1a2558cc)

**4.Decode:**

  - Decodes instructions fetched from memory. It translates instructions into actions for the CPU to execute.
    
    ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/f63e56d0-ad92-4cd0-9ea5-a1806b9e528a)
    
  - Decode with validity:
    
    ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/20a86499-27f9-4c27-9d27-acd72ec8e98b)
    
  - Individual instructions decode:
    
    ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/768596a8-1f36-4244-b279-5da090c2c2cb)

**5.Register File Read:**

  - ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/7b7bb59b-c470-499c-b881-f61e571e05f2)

**6.ALU:**

  - The ALU performs arithmetic and logic operations as directed by the CPU's instructions. It is the computational workhorse of the processor.
    
    ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/a911ffd4-dd20-4104-adda-fe4ad7ef2f2b)

**7.Register File Write:**

  ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/a7b2fb67-4dd2-458f-adfd-8b72763c1e02)

**8.Branch:**

  ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/de94df9f-7415-401a-8c63-4befa1113416)

**9.Checking with Testbench:**

    ![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/cf2424e1-2488-4f34-b037-2f0683205c73)

## Day 5
### Pipelining the CPU
#### Introduction to Control Flow and Read After Write Hazard
**1.Waterfall diagram:**

<img width="446" alt="image" src="https://github.com/GauthamMulay/RISC_V/assets/113660503/8354dd73-716c-4054-980b-1c75b1457bd4">


**2.Control flow hazard:**
- Control flow hazards, also known as control hazards, occur when the normal sequential flow of instructions is disrupted due to conditional branch instructions.
- These hazards can lead to incorrect program execution and reduced performance.
- There are three main types of control flow hazards:
       * Branch Hazards: These occur when a branch instruction (e.g., a conditional jump) is encountered, and the processor is unsure about the branch target. The processor may need to stall the pipeline or make speculative predictions to mitigate the impact of these hazards.
       * Jump Hazards: Jump instructions that cause a change in the program counter can also create hazards, as they affect the instruction fetch stage and can lead to pipeline bubbles (stalls).
       * Return Hazards: Similar to jump hazards, but related to function calls and returns. These can disrupt the flow of instructions.

  
**3.Read After Write Hazard:**
  - Read-after-write hazards, often referred to as data hazards, occur when an instruction depends on the result of a previous instruction that has not yet completed.
- There are three main types of read-after-write hazards:
          * True Data Dependency: This occurs when an instruction (e.g., a load or ALU operation) depends on the result of a previous instruction. The hazard arises because the dependent instruction cannot proceed until the producing instruction has written its result.
          * Anti-Data Dependency: This occurs when a previous instruction depends on a result produced by a later instruction. This situation can cause issues when instructions are executed out of order.
          * Output Data Dependency (Write-After-Read): This happens when two instructions need to read from the same register, and the second instruction wants to read before the first instruction writes to the register. This can lead to incorrect results if not managed properly.

#### LABS
1. Lab to create 3-Cycle Valid Signal:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/2658a400-bcdf-44ef-888c-3a758c01a4bb)

2. 	Modify 3 cycle to distribute logic:
   
 [image](https://github.com/GauthamMulay/RISC_V/assets/113660503/118ba104-5499-4845-863d-6222a7645ad0)

#### Solutions to pipelline hazard:

1.Register file bypass:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/b071e39c-ba5a-4714-bb50-a593367e1d4a)

2.To correct Branch Target path:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/43af164b-f20c-44dd-a8c2-df5592796b66)

3.Instruction Decode:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/1c7a2f1d-014b-4a9b-9057-6aee13ab2a46)

4.Complete ALU:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/8461ab4b-408f-4848-b288-5d013c91be47)

### Load/Store Instructions and Completing RISC-V CPU

1. Lab to redirect loads:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/e939be2f-f840-4809-a658-3484c4a33063)

2. Lab to Data From Memory to Register File:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/44fb6a81-36ca-4493-8ccc-7f23486a5cdd)


3. Lab to Instantiate Data Memory to CPU:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/61267133-1292-482c-ae6a-5771e9575265)

  
4. Lab for Jump Instructions:

![image](https://github.com/GauthamMulay/RISC_V/assets/113660503/9ab0a8fe-0c9f-4e4d-8752-16e12c565012)


## Final RISC-V Core

<img width="264" alt="image" src="https://github.com/GauthamMulay/RISC_V/assets/113660503/f02767c3-c57c-40fc-b8ce-62d1477ba21d">

    

  




