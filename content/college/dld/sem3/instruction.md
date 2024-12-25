1. Computer Registers
2. Computer Instruction
3. Timing & Control
4. Instruction Cycle
5. Register :- Reference instruction
6. Memory :- Reference instruction
7. Input :- Output & interrupt

Program
---
-  A series of instruction that tells the computer about operation, data, order

---
Instruction
---
 A code in binary () that tells the computer to carry out a specific task

---
Instruction cycle
---
1. Reads instruction from memory and places it in a register
2. Decodes the instructions
3. Performs mecessary steps to complete it.
# computer Instruction Set
#  Instruciton code
- A set of bits that guides the computers to perform a specific action.
- A binary code that specifies a sequence of mico-operations for the computer
- It is stored in memory along with data.
- It specifies not only the operation but also the register where the result is stored.
- Parts Instruction code
    1. Operation Code (opcode) :- consists of least n bit for 2^{n} distinct operations
    2. Address (operand)
## Stored Program Organization
- one processor register and an instruction code format with two parts.
- Instruction code | Data
- eg 4096 words -> $2^{12} = 4096$ hence 12 bit for address + 4 bit for opcode = 16 bit binary operand
## indirect address
- address bits in binary operand has a memory address inside which the address of operand resides
-  12 bit address + 3 bit operation code + 1 bit for address mode
- if addressing mode bit is 0 -> direct ; 1 -> indirect
## direct address
- address bits in binary operand holds address of operand

# Computer Registers
- they are used for storing the instruction code after it is read from memory
- also for manipulating data and holding a memory address
- Types of register are

1. Address Register (AR) --> 12 bit
---
- Memory's address for current instruction.
---
2. Program Counter (PC) --> 12 bit
---
- memory's address but for next instruction.
---
3. Input Register (INPR) --> 8 bit
---
- register for an input device
---
4. Output Register (OUTR) --> 8 bit
---
- register for an output device
---
5. Accumulator (AC) --> 16 bit
---
- This is the most frequently used register used to store data taken from memory.
---
6. Data Registers (DR) --> 16 bit
---
- It contains data to be written into or to be read out from the addressed location.
---
7. Instruction Register (IR) --> 16 bit
---
- The IR holds the instruction which is just about to be executed.
- The instruction from the PC is fetched and stored in IR.
---
8. Temporay Rgister (TR) --> 16 bit
---
- A temporary register is a storage space that holds data while it is being processed by the CPU
---
# Common Bus System
- Use for transferring information in a system of many registers with max efficiency
- The outputs of 7 registers and bus are connected to it.
- Select lines are used for selecting different registers and put data to bus
- data is loaded to register from bus whose load (LD) is enabled.
- the memory recives or gives its contents when it Write or Read is enabled respectivly
- when the content of AR & PC are loaded to bus the 4 bits (opcode + adressing mode bit) becomes 0000.
- when AR & PC receives information from the bus 12 bit address is transferred into the register.
# Instruction set completness
- if the computer includes a sufficient number of instructions in each of the categories below.
1. Input and Output instructions
2. Program control Instruction with status conditions checking instructions.
3. Data Transfer Instruction
4. Data Manipulation Instructions (Arithematic, Logical, Shift)
# Timing and Control
- Master clock generator controls timing of all registers
- Until registers are not enabled by control signal the clock pulses don't change state.
- Control Unit generates contorl signals
- 2 organisations generate control signals for control unit

|Category|Hardwierd Contorl Unit|Micro-programmed Control Unit|
|-|-|-|
|Speed|fast|slow|
|Cost|expensive|cheaper|
|Flexibility|NO|YES|
|decoding|Complex|Simple|
|microprocessor|RISC|CISC|
|area for chip|less|more|
|Control memory|present|absent|


1. Hardwired Control Unit
---
- They are implimented through use of sequential logical units, gates, flip-flop, decoders.
---
2. Micro-programmed Control Unit
---
- They are implimented through use of micro-operations
---
# Control Unit
- It controls the flow of data between processor, memory, and peripherals
- Along with IR decodes the instructions and generate control signals
- It generates Timing and control signals to all operation in the computer
- Functions
    1. Sequencing :- creating proper sequence of micro-operations based on the task executing
    2. Execution :- Executing each micro-operations
- It is done through control signals
- Program(one) --> Instruction cycle(multiple) --> (phasese) Fetch, Decode, Execute, Interrupt --> micro-operations.
- 4 inputs :- Flags, Clock, Instruction register, Control signal from bus
- 2 output :- control signal within CPU, to contol bus


## Control Unit Architecture
1. Instruction Register
2. Two decoders
3. Number of Control Logic Gate
4. 4 bit sequence counter

# Instruction cycle
- A program consists of a sequence of instruction.
- Instructions are executed in a cycle
- Each instruction cycle consists of the following phase
1. Fetch instruction from memory
2. Decode the instruction
3. Read the effective address from memory if the instruction has an indirect address
4. Execute the instruction
## instruction set architecture
- ISA acts as an medium or interface between hardware & software
- 2 Types of ISA
1. RISC (Reduced Instruction Set Computer)
2. CISC (Complex Instruction Set Computer)


|Base|RISC|CISC|
|-|-|-|
|Focus|Software|Hardware|
|Addressing mode|Less|More|
|Space in RAM|More|Less|
|Instruction Format|fixed|variable|
|Power Consumption|Low|High|
|Number of registers|More|Less|
|Instruction per clock cycle|One per One|One per Many|
|Execution Time|very short|slightly more|
|Example|ARC,ARM,Alpha|Motorola 6800|

## Phases

|Basis|Horizontal|Vertical|
|-|-|-|
|contol word support|longer|short|
|degree of parallelism|High|Low|
|Additional hardware|NO|Yes(decoders)|
|Speed|Fast|Slow|
|Flexibility|More|Less|
|Type of micro-instruction|horizontal|vertical|
|Use Ram encoding|Less|More|

## register reference instruction
- Register-reference instructions are recognized by the control when D7 = 1 and I=0.
- These instructions use bits 0 through 11 of the instruction code to specify one of 12 instructions.
- These 12 bits are available in IR (0-11).

### AND to AC:
- This is an instruction that performs the AND logic operation on pairs of bits in AC and the memory word specified by the effective address.
- The result of the operation is transferred to AC.
- The microoperations that execute this instruction are:
    - D0T4:DR<-M[AR]
    - D0T5:AC<-AC^DR,SC<-0
### ADD to AC:
- This instruction adds the content of the memory word specified by the effective address to the value of AC.
- The sum is transferred into AC and the output carry Cout is transferred to the E (extended accumulator) flip-flop.
- The microoperations needed to execute this instruction are LDA:
    - D1T4 : DR <- M[AR]
    - D1T5 : AC <- AC + DR, E <- Cout, SC <- 0
### LDA: Load to AC
- This instruction transfers the memory word specified by the effective address to AC.
- The microoperations needed to execute this instruction are
    - D1T4 : DR <- M[AR]
    - D1T5 : AC<-AC+DR, E<-Cout,SC<-0

### STA: Store AC
- This instruction stores the content of AC into the memory word specified by the effective address.
- Since the output of AC is applied to the bus and the data input of memory is connected to the bus,
- we can execute this instruction with one microoperation.
    - D3T4: M[AR]<-AC,SC<-0
### BUN: Branch Unconditionally
- This instruction transfers the program to the instruction specified by the effective address.
- The BUN instruction allows the programmer to specify an instruction out of sequence and we say that the program branches (or jumps) unconditionally.
- The instruction is executed with one microoperation:
    - D4T4: PC <-AR, SC <-0

### BSA: Branch and Save Return Address
- This instruction is useful for branching to a portion of the program called a subroutine or procedure.
- When executed, the BSA instruction stores the address of the next instruction in sequence (which is available in PC)
- into a memory location specified by the effective address.
- The effective address plus one is then transferred to PC to serve as the address of the first instruction in the subroutine.
- This operation was specified with the following register transfer:
    - M[AR]<-PC,PC<-AR+1
