# I/O interface
- Problems with I/O:
    1. Peripherals are electromechanical & electromagnetic devices and are interacting with electronics devices(CPU).
    2. Data transfer rate of peripherals is usually slower than transfer rate of CPU.
    3. Data codes and formats in peripherals differ from word format in CPU
    4. Operating modes of peripherals are different from each other and each one must be controlled without disturbing other.
- To resolve these differences, computer system includes Interface units between CPU and peripherals
----
- I/O interface provides a method for transferring information between internal storage and external I/O devices.
- It supervise and synchronize all input and output transfers
- When the interface detects it own address, it activates path between bus lines and the device.
- At the time address is made available in address lines, the processor provides function code(I/O command) in the control lines.
- Types of I/O command:
    1. Control command: To activate and inform what to do.
    2. Status command: To test various status conditions.
    3. Data Output data: It causes the transfer of data from bus into one of its registers.
    4. Data Input Command: Interface receives data from peripheral and places them on buffer register where it is put into data lines.

## connection of i/o
- Each peripheral has its own controller that operates a particular electromechanical device.
- To communicate with a particular device, the processor places a device address on the address lines.

#  I/O  v/s memory bus
- In addition to communicating to I/O, processor must also communicate with memory unit.
- There are three ways that computer buses can be used to communicate with memory and I/O:
    1. IOP :- Use two separate buses, one for memory and one for I/O.
    2. Isolated I/O :- Use one common bus for both memory and I/O but have separate control lines for each.
    3. Memory mapped I/O :- Use one common bus for memory and I/O with common control lines.
## Isolated I/O
- we Have common bus(data and address) for I/O and memory but separate read and write control lines for I/O.
- The address space of memory and I/O is isolated.
- The address for I/O here is called ports.
- Here we have different read-write instruction for both I/O and memory.
- I/O read and I/O write are enabled during I/O transfer and Memory read/write are enabled during memory transfer.
- each of the instructions will be associated with address of the interface register.
- When the CPU fetches and decodes the I/O instruction,
    - it places the address associated with the instruction on the common address lines
    - enables I/O read or I/O write control line.
- When the CPU fetches and decodes the Memory instruction,
    - it places the address associated with the instruction on the common address lines
    - enables Memory read or Memory write control line.
## memory mapped I/O

- In this case every bus is common due to which the same set of instructions work for memory and I/O.
- Hence we manipulate I/O same as memory and both have same address space,
- due to which addressing capability of memory become less because some part is occupied by the I/O.
- The assigned address cannot be used for storing memory words, which reduces memory address range available.
- there are no specific, input or output instruction.
- CPU manipulate I/O data residing in interface registers with the same instruction used to manipulate memory words.
- Load and store instruction used for reading/writing  from memory and can be use for input or output data from I/O instruction.
- With memory-mapped I/O all instructions that refer to memory are also available for I/O.

# Modes of transfer
## programmed I/O
- Programmed I/O operations are the result of I/O instructions.
- Each data item transfer is initiate by an instruction in the program.
- Usually the transfer is to and from a CPU register and peripheral.
- Other instructions are needed to transfer data between memory and CPU.
- Once a data transfer is initiated, the CPU is required to monitor the interface to see when a transfer can again be made.

## Interrupt Initiatted I/O
- In the programmed I/O CPU stays in program loop until the I/O indicates that it is ready for data transfer.
- This is time consuming process since it makes CPU busy needlessly.
- This can be avoided by using an interrupt facility.
- When the interface determines that device is ready for data transfer, it generates an interrupt request.
- Upon detecting external interrupt signal, the CPU momentarily stops the task it is processing.
- It then branches to fulfill the I/O request and return to the original task.
- Based on the concept of Priority Interrupt.

## Direct Memory Access (DMA)
- The transfer of data between a fast storage device such as magnetic disk and memory often limited to the speed of CPU.
- Removing the CPU and letting the peripheral device manage the memory bus directly improve speed of transfer.
- Such transfer technique is called Direct Memory Access (DMA).
- A DMA controller takes over the buses to manage the transfer directly between I/O device and memory.
- During DMA transfer, the CPU is idle and has no control over memory buses.
- By using Bus Request(BR) and Bus Grant(BG) the buses are released to DMA controller.
- Data transfer ways:
    1. Burst Transfer: Here number of words are transferred in a block. Example: Magnetic disk.
    2. Cycle stealing: Allows the DMA controller to transfer one data word at a time after it must return the control of buses to CPU.
### initialization
- The CPU initializes the DMA by sending the following information through the data bus.
- The starting address of the memory block where data are available(for read) or where data are to be stored(for write).
- The word count, which is the number of words in the memory block.
- Control to specify the mode of transfer such as read or write.
- A control to start the DMA transfer.
# I/O Transfer
- An IOP takes care of input and output tasks.
- IOP is similar to CPU except IOP can fetch and execute an I/O instruction.
- CPU is usually assigned task of initiating the I/O program and thus IOP.
- The CPU is assigned the task of initiating all operations, but I/O instructions are executed in IOP.
- When an I/O operation is required, the CPU informs the IOP where to find the I/O program and then leaves the transfer details to the IOP.
- CPU instructions also test I/O status conditions needed for making decisions on various I/O activities.
- IOP is also responsible of taking care of data synchronization, formats etc between CPU and I/O devices.
- In most computers CPU is master and IOP is slave.
- The IOP typically asks for CPU attention by means of Interrupt.
# BUS
1. Data Bus: Bi-directional and transfers data.
2. Address Bus: Uni-directional and sends the address.
3. Control Bus: R/W, BR,BG etc.


## bus arbitation
- The device that is allowed to initiate data transfers on the bus at any given time is called Bus master.
- Bus arbitration is the process by which the next device becomes Bus master and will do the data transfer.
- Two approaches: Centralized Arbitration and Distributed Arbitration.
# Types of Interrupts
1. External Interrupt
---
- It comes from I/O devices, from timing device, or from any other external source.
---
2. Internal Interrupt:
---
- It includes register overflow, invalid operation code, stack overflow etc.
---
3. Software Interrupt or Hardware Interrupt:
----
- External and Internal interrupts are initiated from signals that occur in the hardware of the CPU.
- A software interrupt is initiated by executing an instruction.
---
4. Priority Interrupt
---
- In case several sources will request service simultaneously,
- in this case system must decide which device to service first. For ex: Polling, Daisy Chain.
# Data transfer
- Internal operations in a digital system are synchronized by means of clock pulses supplied by common pulse generator.
- If the registers in the interface share a common clock with the CPU registers, the transfer is synchronous.
- Asynchronous data transfer requires that control signals be transmitted between communicating units
    - it indicate the time at which data is being transmitted.
- Asynchronous data transfer can be accomplished by Strobe & Handshaking.
## Strobe control:
- It employs single control line.
- It can be activated either by source or destination unit.
## handshaking
- Source Unit --> Destination Unit {Data bus; Data valid}
- Destination Unit --> Source Unit {Data accepted}
- Source unit place data on the bus. Enable data valid
- Destination unit Accepts data from the bus. Enable data accepted
- Source Unit Disable data valid. Invalidate data on the bus
- Destinaation unit disable data accepted. ready to accept data (inital state).
- Source unit place data on the bus. Enable data valid








