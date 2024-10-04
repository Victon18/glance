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
- **TEXT** -> It contains the code that the process executes
- **STACK** -> It stores instructions and global variable for active procedure call.
- **DATA** -> It stores the global variables and dynamically allocated memory that
process uses during execution.
- **HEAP** -> Heap containing memory dynamically allocated during run time

# PCB
Each process is represented in the OS by a PROCESS CONTROL BLOCK (PCB)- also called Task control Block.
When the process makes a transition from one state to another, the operating system must update information in the process’s PCB.
A process control block (PCB) contains information about the process, i.e. registers, quantum, priority, etc.
The process table is an array of PCBs, which logically contains a PCB for all of the current processes in the system.
Hardware instructions are often available that load state information into the PCB and restore the information quickly

Parts of program counter
-----

- Pointer
---
It is a stack pointer that is required to be saved when the process is switched
from one state to another to retain the current position of the process.

---
- Process state:
---
It stores the respective state of the process. The state may be New, Ready, Running, Waiting, Halted and so on.

---
- Process number:
---
Every process is assigned a unique id known as process ID or PID
which stores the process identifier.

---
- Program counter:
---
Program Counter stores the counter, which contains the address of
the next instruction that is to be executed for the process.

---
- CPU Register:
---
Registers in the PCB, it is a data structure.
The registers vary in size, numbers and type depending on the computer architecture.
They include accumulator, index registers, stack pointer and general purpose register and any conditional code information.

---
- Memory Allocations Information:
---
This field contains the information about memory management system used by the operating system. This may include page tables, segment tables, etc.
This information may include the value of the BASE and LIMIT registers, page table, or segment tables depending on the memory system used by OS.

---
- CPU scheduling Information:
---
This includes a process priority, pointers to scheduling queues and any other scheduling parameters.

---
- Accounting Information :
---
This includes the amount of CPU and real time used, time limits, account numbers, job and process number and so on…

---
- I/O status Information:
---
The information includes the list of I/O devices allocated to this process, a list of open files and so on.
1. List of Open files:
	This information includes the list of files opened for a process.


![[pcb.png|300]]
# process state diagram

- NEW: The Process is being created.
- READY: Process is competing for the CPU. Process is ready and waiting for processor’s
turn.
- RUNNING: Process is currently being executed. OS allocate all H/W and S/W resources
to the process.
- WAITING: Process is waiting for some I/O device and for event to occur in the queue.
- EXIT: A process is completed and releases all the allocated resources.

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
It is the activity of the process manager that handles the removal of the running process from the CPU
and the selection of another process on the basis of a particular strategy.

Dispatcher
---
The dispatcher is the module that gives control of the CPU to the process selected by the short-term scheduler.
This function involves:
- Switching context
- Switching to user mode
- Jumping to the proper location in the user program to restart that program from where it left last time.

## types of process (Multiprocessing)
1. **Pre-emption** – Process is forcefully removed from CPU.
    - pre-emtion happens because of two factors time quantum and priority
    - Pre-emption is also called as time sharing or multitasking.
2. **Non pre-emption** – Processes are not removed until they complete the execution.

## CPU Scheduling: Scheduling Criteria
- Throughput:
---
It is the total number of processes completed per unit time.
This may range from 10/second to 1/hour depending on the specific processes.

---
- Turnaround Time:
---
It is the amount of time taken to execute a particular process, (Wall clock time).

---
- Waiting Time:
---
The sum of the periods spent waiting in the ready queue amount of time a process has been waiting in the ready queue.

---
- Load Average:
---
It is the average number of processes residing in the ready queue waiting.

---
- Response Time:
---
Amount of time it takes from when a request was submitted until the first response is produced.
Remember, it is the time till the first response and not the completion of process execution (final response).

----
- CPU Utilization:
---
To make out the best use of CPU and not to waste any CPU cycle,
In general CPU utilization and Throughput are maximized and other factors are reduced for proper optimization.

---
## process scheduler
- Process scheduler selects among available processes for next execution on CPU core
- **Goal** -- Maximize CPU use, quickly switch processes onto CPU core
- Maintains scheduling queues of processes
- types of schduler
    1. Long-Term Scheduler
    2. Short-Term Scheduler
    3. Medium-Term Scheduler

- Long term – performance
---
Makes a decision about how many processes should be made to stay in the ready state, this decides the degree of multiprogramming.
Once a decision is taken it lasts for a long time hence called long term scheduler

---
- Short term – Context switching time
---
Short term scheduler will decide which process to be executed next and then it will call dispatcher.
A dispatcher is a software that moves process from ready to run and vice versa

---
- Medium term – Swapping time –
---
Suspension decision is taken by medium term scheduler.
Medium term scheduler is used for swapping that is moving the process from main memory to secondary and vice versa
Swapped out :
    To remove the process from memory and make space for other processes, the suspended process is moved to the secondary storage.
Swap in:
    the process can be reintroduced into memory and its execution can be continued where it is left off.

---

Differences

| Long-Term Scheduler                                                     | Short-Term Scheduler                                       | Medium-Term Scheduler                                                       |
| ----------------------------------------------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------------------------- |
| It is a job scheduler                                                   | It is a CPU scheduler                                      | It is a process swapping scheduler.                                         |
| Speed is sloweer than short term scheduler                              | Speed is fastest among other two                           | Speed is in between both short and long term scheduler.                     |
| It controls the degree of multiprogramming                              | It provides lesser control over degree of multiprogramming | It reduces the degree of multiprogramming.                                  |
| It is almost absent or minimal in time sharing system                   | It is also minimal in time sharing system                  | It is a part of Time sharing systems.                                       |
| It selects processes from pool and loads them into memory for execution | It selects those processes which are ready to execute      | It can re-introduce the process into memory and execution can be continued. |

### scheduling queues

- Ready queues
---
set of all processes residing in main memory, ready and waiting to execute,
This queue is generally stored as a linked list.
A ready queue Header will contain pointers to the first and last PCB of the list.
Each PCB has a pointer field that points to the next process in the ready queue.

---
- Device queue / Wait queue
---
The list of processes waiting for a particular I/O device is called a Device Queue.
Each device has its own Device Queues.

---

- A new process is initially put in the ready queue.
- It waits in the ready queue until it is selected for execution (Dispatched) and is given the CPU.
- Once the CPU is allocated to the process and is executing one of the several events could occur:
	i. The process could issue an I/O request and then be placed in I/O Queue.
	ii. The process could create a new sub process and waits for its termination.
	iii. The Process could be removed forcibly from the CPU as a result of interrupt, and
be put back in the ready queue.
- In the first two cases, the process eventually switched from the waiting state to the ready state, and is then put back in the ready queue.
-A process continues this cycle until it terminates, at which time it is removed from the queues and has its PCB and resources reallocated.

# Context Switch

- When CPU switches to another process
- the system must save the state of the old process and load the saved state for the new process
- Context-switch time is pure overhead; the system does no useful work while switching
- complexity of OS and the PCB $\varpropto$ time in context switch
- Some hardware provides multiple sets of registers per CPU ie multiple contexts loaded at once

![[context.png]]

