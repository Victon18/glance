# register transfer language
The symbolic notation used to describe the microoperation transfers among registers is called Register transfer language.

Microoperations
---
The operations executed on data stored in registers are called microoperations.

---

Register transfer
---
The term Register transfer implies the availability of hardware logic circuits to perform stated microoperation.
Computer registers are designated by capital letters to denote the function of register.
The information transfer from one register to another register is designated in symbolic form.

- Types

    1. Instruction register (IR)
    2. Program counter (PC)
    3.  General-purpose register (R0 -> Rn-1)
    4.  Memory address register (MAR)
    5.  Memory data register (MDR)

Register transfer under a predetermined control condition can be represented by an if-then statement :
    If (P=1) Then R2 -> R1
where P is a control signal generated in the control section.
    It can be written as P: R2 -> R1

# Bus Transfer
A group of lines that serves as a connecting path for several devices is called a bus.
The efficient way for transferring information between registers in a multiple-register configuration is a common system bus.
One way of constructing a common bus system is with multiplexers

When the bus is included in the statement, the register transfer is symbolized as follows:
    BUS -> C, R1 -> BUS
The content of register C is placed on the bus and
the content of the bus is loaded into register R1 by activating its load control input.

If the bus is known to exist in the system, it may be convenient just to show the direct transfer.
    R1 -> C

### Thee-state Bus Buffers:
Two of the states are signals equivalent to logic 1 and 0 as in a conventional gate.
The third stage is a high-impedance state which behaves like an open circuit.
The most commonly used in the design of a bus system is the buffer gate.

# Memory tranfer
A memory word will be symbolized by the letter M.

Address
---

memory unit that receives the address from a register called address register (AR)

---
Data
---
Data transferred to another register called data register (DR).

---

Read operation
---
The transfer of information from a memory world to the outside environment is called a read operation.
The read operation can be symbolized by:
    `Read : DR -> M[AR]`
This causes a transfer of information into DR from the memory word M selected by the address in AR.

----
Write operation
----
The transfer of new information to be stored into the memory is called a write operation.
The write operation transfers the content of a data register like R1 to memory word M selected by address.
    `Write: M[AR] -> R1`
This causes a transfer of information from R1 into the memory word M selected by the address in AR.

---

