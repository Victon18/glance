# process
- Program becomes process when an executable file is loaded into memory
- A process contains memory area, local, global variable, CPU registers, Program Counters
- Process requires a set of resources, including a processors, program counters, registers to perform its functions
- Multiple process may associate with one program
- Program is passive entity stored on disk (executable file); process is active

# type of process
- **CPU Bound Process**: If the process is intensive in terms of CPU operations.
- **I/O Bound Process**: If the process is intensive in terms of I/O operations.


# parts of process
- **TEXT** -> The program code, also called text section
- **STACK** -> Stack containing temporary data like Function parameters, return addresses, local variables
- **DATA** -> Data section containing global variables
- **HEAP** -> Heap containing memory dynamically allocated during run time

# PCB
Each process is represented in the OS by a PROCESS CONTROL BLOCK (PCB)- also called Task control Block.
When the process makes a transition from one state to another, the operating system must update information in the process’s PCB.
A process control block (PCB) contains information about the process, i.e. registers, quantum, priority, etc.
The process table is an array of PCBs, which logically contains a PCB for all of the current processes in the system.

Parts of program counter
-----

- Pointer: It is a stack pointer that is required to be saved when the process is switched
from one state to another to retain the current position of the process.

- Process state: It stores the respective state of the process.

- Process number: Every process is assigned a unique id known as process ID or PID
which stores the process identifier.

- Program counter: Program Counter stores the counter, which contains the address of
the next instruction that is to be executed for the process.

- CPU Register: Registers in the PCB, it is a data structure. When a processes is running and it’s time slice expires, the current value of process specific registers would be stored in the PCB and the process would be swapped out. When the process is scheduled to be run, the register values is read from the PCB and written to the CPU registers. This is the main purpose of the registers in the PCB.
- Memory Allocations: This field contains the information about memory management system used by the operating system. This may include page tables, segment tables, etc.
- List of Open files: This information includes the list of files opened for a process.


![[pcb.png|300]]
# process state diagram

## 5 state

![[5stage.png]]
### process names
1. **Awake**: New -> Ready
2. **Dispatch**: Ready -> Running
3. **Timer-runout**: Running -> Ready
4. **Block**: Running -> Blocked
5. **wakeup**: Blocked-> Ready

## 7 state

![[7stage.png]]

# process scheduling
## types of process (Multiprocessing)
1. **Pre-emption** – Process is forcefully removed from CPU.
    - pre-emtion happens because of two factors time quantum and priority
    - Pre-emption is also called as time sharing or multitasking.
2. **Non pre-emption** – Processes are not removed until they complete the execution.

## process scheduler
- Process scheduler selects among available processes for next execution on CPU core
- **Goal** -- Maximize CPU use, quickly switch processes onto CPU core
- Maintains scheduling queues of processes
- types of schduler
    1. Long-Term Scheduler
    2. Short-Term Scheduler
    3. Medium-Term Scheduler

### scheduling queues
- **Ready queues** – set of all processes residing in main memory, ready and waiting to execute
- **Wait queues** – set of processes waiting for an event (i.e., I/O)
Processes migrate among the various queues

# Context Switch
- When CPU switches to another process
- the system must save the state of the old process and load the saved state for the new process
- Context-switch time is pure overhead; the system does no useful work while switching
- complexity of OS and the PCB $\varpropto$ time in context switch
- Some hardware provides multiple sets of registers per CPU ie multiple contexts loaded at once

![[context.png]]

