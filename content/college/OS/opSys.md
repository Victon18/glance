# operating system
- A program that acts as an intermediary between a user of a computer and computer hardware”
“Operating system controls and coordinates the use of the hardware among various applications programs for various users”
“The operating system is the one program that is running all times on the computer (usually
called the Kernel), with all else being application program.

Primary Goal: Convenience of use (For small PCs)
Secondary Goal: Efficient utilization of hardware (for large, shared and multiuser systems).

Components of OS
    1. Hardware : CPU, Memory, I/O Services
    2.  Operating System:
    3.  Applications program
    4.  Users
# Terminologies
1. Multipromming:- RAM (primary memory ) having multiple programmes in its queue
---
2. Multitasking:- CPU time is divided into minute interval
    - time sharing:- Each interval is allocated to each process and the cycle repeats
---
3. Multiprocessing:- Simultaneous or parallel execution of more than one program on more than one CPU,*Parallelism*
---
4. Multiuser:- If OS support multiple user to simultaneously execute their program on single common shared OS.
---
5. Multithreading:- Simultaneously execution of more than one threads
   - threads :- Sub process(Sub part) of a process/program like sum,difference of a calculator program
   - child process(thread); parent process(main program)
   - orphan process
---
6. System Call:- build in defined system function
- used by application program to request services of OS
- System calls provide an interface to the services made available by an operating system.
- Fork() system call
---

# Functions of OS
- Provide environment whithin which other programs can work
- Memory Management:- Allocation and De-allocation of memory
- Processor Management:- Keeps tracks of processor and status of process ie traffic controller.
- Device Management:- Keeps tracks of all devices ie I/O controller.
- File Management:- Keeps track of information, location, uses, status etc ie file system.
- It controls the execution of program

![[system.png|300]]

---
# components of OS
1. Process Manager
----
A process needs certain resources, including CPU time, memory, files, and I/O devices, to accomplish its task.
Process Manager performs following activities for an Operating System:
    - The creation and deletion of both user and system processes
    - The suspension and resumption of processes.
    - The provision of mechanisms for process synchronization
    - The provision of mechanisms for deadlock handling.

---
2. Main Memory Manager
---
Memory is a large array of words or bytes, each with its own address.
It is storage of quickly accessible data shared by the CPU and I/O devices.
Main memory is a volatile storage device.
Main Memory Manager performs following activities for Operating System:
    - Keep track of which parts of memory are currently being used and by whom.
    - Decide which processes are to be loaded into memory when memory space becomes available.
    - Allocate and de allocates memory space as needed.

---
3. File Manager
---
A file is a collection of related information defined by its creator.
File Manager performs following tasks for an Operating System
    - The creation and deletion of files.
    - The creation and deletion of directory.
    - The support for manipulating files and directories.
    - The mapping of files onto disk storage.
    - Backup of files on stable (nonvolatile) storage.
    - Protection and security of the files.

---
4. Secondary Storage Manager
--
Secondary storage includes CD-ROM, hard disks, pen drives etc.
Secondary Storage Manager performs following tasks for an Operating System
    - Free space management
    - Storage allocation
    - Disk Scheduling

---
5. I/O Manager
---
The I/O system consists of a buffer-caching system, a general device-driver interface or the drivers for specific hardware devices.
I/O Manager performs following tasks for an Operating System
    - Managing buffer caching system
    - To activate a general device driver code
    - To run the driver software for specific hardware devices as and when required.

---
6. Networking Manager
---
The processors distributed OS in the system are connected through a communication network.
Networking Manager performs following tasks for an Operating System
    - Setup of a networking connection (Wireless & LAN)
    - Mechanism for maintaining IP Address (Manual & by using DHCP)
    - Managing networking protocol
    - Security of network connection
    - Firewall management for blocking unauthorized access of computer

---
7. Protection System Manager
---
Protection refers to a mechanism for controlling access by programs, processes, or users to both system and user resources.
Protection System Manager performs following tasks for an Operating System
    - Provides a mechanism for controlling the access of programs, processes, or users to the resources defined by a computer controls.
    - Improve reliability by detecting latent errors at the interfaces between component subsystems.
    - Early detection of interface errors to prevent healthy subsystem by a subsystem that is malfunctioning.
    - Provide a mean of authentication and authorization

---
8. Command Interpreter
---
Command-Interpreter system is a system program, which is the interface between the user and the operating system.
Command Interpreter performs following tasks for an Operating System
    - Provides a mechanism to read command from user or process.
    - Interpret command into low level language
    - Interact with required hardware, resource or file.
    - Generate output defined in the command.


Bootstrapping
---
- Booting is the process of loading operating system into main memory.
- During bootstrapping, the kernel is loaded into memory and begins to execute.
- A variety of initialization tasks are performed and the system is made available for the users.
- Bootstrap program
    The primitive loader program that can load and execute the Boot program is called Bootstrap Program.
    Bootstrap program is generally stored in ROM.
    On- Start up, the computer automatically reads the bootstrap program.
This primitive loader is then executed and loads the boot program in predefined memory location.
The boot program is generally stored on the disk with predefined address, called **boot sector**.
The boot program then loads the operating system into memory.

# types of OS
1. Early Computers
---
- Large Machine Run from the Console.
- The programmer would write and operate the program directly from operator’s console.
- Program would be loaded manually into memory from the paper tape or from the punch card.
- Button pushed to set the starting address and to start the execution of the program.
- The programmer monitors its execution by the display lights on the Panel.
- If error has occured, examine the contents of the memory and registers and debug the program directly from the console.
- Output was printed or was punched onto paper tape or card for later processing.
---
2. Simple Batch Systems ( Resident Monitor)
---
- Jobs with similar needs were batched together and run through the computer as group.
- Automatic job sequencing: This was procedure for automatically transferring control from one job to the next.
- Resident monitor was created for this automatic job scheduling . It resided in the memory.
-

Problmes
---
OVERLAPPED CPU and I/O: --
Even with automatic job sequencing, the CPU is often idle.
The problem is the speed of the mechanical I/O devices which are intrinsically slower than electronic device.

Solution
---
1. Off-Line Processing :
---
- Replacement of the very slow card readers and line printers with magnetic tape unit.
- the cards were first copied onto a magnetic tape via a separate device.
- When the tape was sufficiently full, it was taken down and carried over to the computer.
- input read from tape; output printed to tape
- Main advantage the main computer was no longer constrained by the speed of the card readers and line printers but was limited by only the speed of the much faster magnetic tape units.

2. Spooling ( Simultaneous Peripheral Operation On-Line):
---
- Random-Access Device like disk system was introduction.
- In disk system, cards are read directly from the card reader onto the disk.
- Location of card images is recorded in a table kept by the operating system.
-  When a job is executed, the OS satisfies its requests for card reader input by reading from the disk.
-  when the job requests the printer to output the line, tht line is copied into a system buffer and is written to the disk.
-  When the job is completed, the output is actually printed.
-  Spooling overlaps the I/O of one job with the computation of other jobs.
-  Spooling has a direct beneficial effect on the performance of the system
-  Spooling can keep the CPU and the I/O devices working at same time at much higher rates.
---
3. Multiprogramming OS
---
- Multiprogramming increases CPU utilization by organizing jobs so that the CPU always has something to execute.
- The OS keeps several jobs in memory at a time which is subset of the jobs kept in the job pool.
- The OS picks and begins to execute one of the jobs in the memory.
- The OS switches to and executes another job, when one job needs to wait for some I/O operation.
- job scheduling is here.
- disk and memory management is here.
- CPU Scheduling is here.
---
4. TIME SHARING SYSTEMS (Multitasking)
---
-  Time sharing (Multitasking) is a logical extension of multiprogramming.
-  An interactive or hands on computer system provides On-line communication between the user and the system.
- input keyboard; output monitor;
- When the OS finishes the execution of one command it seeks the next.
- An on-line file system was available; the file may be free form such as text files or rigidly formatted.
- An interactive system is used when a short response is required.
- CPU scheduling and multiprogramming to provide each user with a small portion of a time shared computer.
- Each user has at least one separate program in memory.
- It allows many users to share the computer simultaneously.
- It provides mechanism for concurrently execution, which requires sophisticated CPU scheduling scheme.
- synchronization & deadlock management.
---
5. PERSONAL COMPUTER SYSTEM (PCs)
----
- These systems were dedicated to single user.
- They are micro computers, considerably smaller and less expensive than main frame systems.
- Lacking the features needed to protect an operating system from user program.
- Neither multi user nor multi tasking.
- Goal of these OS have changed with time, instead of trying to maximize CPU and peripheral utilization,
- the system opt for user convience and responsiveness.
---
6. PARALLEL SYSTEMS: (Multi-Processing)
---
- Having more than one processor in close communication sharing the computer bus, the clock and sometimes memory and peripheral devices.
- These systems are referred as tightly coupled systems.
- One Advantage is increased throughput.
- Affordable
- Reliable
-  System designed for graceful degradation is called “Fail-Soft”.
- “Tandem System” uses both Hardware and Software duplication to ensure continued operation despite faults.
- The system consists of two identical processors, each with its own local memory and connected by a bus.
- One processor is called Primary and other is called Backup or Secondary processor.
- Two copies are kept of each process; One for primary and other for Secondary.
- If Failure is detected, the backup copy is activated and is restarted from the most recent checkpoint.

Types:
i. Symmetric Multiprocessing :
-  Each processor runs an identical copy of the OS and copies communicate with one another as needed.
- Each processor performs all tasks within OS.
- All Processor are Peer and no Master Slave relationship exists.
-  In Symmetric Multiprocessing treats all processors as equals and no I/O can be processed on any CPU.
ii. Asymmetric Multiprocessing
- Each processor is assigned a specific task.
- A master processor controls the system. The other processors look to the master for instructions or predefined task. Thus, this defines master-slave relationship.
-  Master Processor schedules and allocates the work to the slave processor.
- Each processor has its own address space.
---
8. Distributed System:
---
- Distribute computation among several processors.
- The processor does not share memory or a clock. Instead each processor has its own local memory
- The Processor communicates with one another through various communications line such as high speed buses and telephone lines.
- These systems are usually referred as Loosely Coupled Systems.
- The processors may vary in size and functionality. These processors are refered as sites, nodes and computers.

Advantages:
i. Resources Sharing:
    - Sharing and printing files at remote sites
    - Processing information in a distributed database – using remote specialized hardware devices
ii. Computational Speed up:
    - Computation can be partitioned into number of subcomputations that can run concurrently.
    -  Distributed system allow to distribute the computation among the various sites to run that computation concurrently.
iii. Reliability :
    - via redundancy either in both hardware or data
    - The failure of a site must be detected and recovered by the system
iv. Communication:
    - Numbers of sites are connected to each other via communication network.

Difference between symmetric multiprocessing and asymmetric multiprocessor operating
---
Symmetric Multiprocessing treats all processors as equals and no I/O can be processed on any CPU while
Asymmetric Multiprocessing has one master CPU and the remainder CPUs are slave.
The master distribute tasks among the slave processors and I/O usually done be master only.
Processors at different sites have the opportunity to exchange information through file transfers, message passing or e-mails.

---
9. REAL TIME SYSTEMS
---
- It is used when there are rigid time requirement on the operation of a processor or
the flow of data and the thus is often used as a control device in a dedicated
application.
- They tend to have very specific tasks. They have no user interface.
- Sensors bring data to the computer.
- The computer must analyze the data and possibly adjust controls to modify the sensor input.
- These systems are embedded system where the tasks are already integrated in circuits which executed without an OS.
- It has well defined fixed time constraints.
- Processing must be done within the defined constraints or the system will fail.
There are two types of Real Time Systems:
i. Hard Real Time System:
    - It guarantees that critical tasks complete on time.
    - This goal requires that all delays in the systems be bounded from the retrieval of stored data.
    - Secondary Storage of any sort is limited or missing with data instead being stored in short term memory or in Read Only Memory (ROM)
    - Virtual Memory is almost never found on real time system.
ii. Soft Real Time System:
    - Less restrictive than hard real time system.
    - In this a critical task gets priority over other tasks and retain that priority until it completes.
    - As in Hard real time system, kernel delays still need to be bounded.
    - Soft real time is an achievable goal that is amenable to mixing with other type of system
    - It has more limited utility than Hard Real time system.
    - Given their lack of deadline support, they cannot be used for industrial control and robotics.
    - These systems need advanced operating System features that cannot be supported by hard real time systems.
    - Because of the expanded uses for the Soft real time functionality, it is finding its way into most recent OS.
    - It is less stringent timing constraints and do not support deadline scheduling

# Architectures of OS
### Simple
MS-DOS device drivers are collections of routines in memory that interact with hardware devices.
It provides the most functionality in least space.

- Disadvantages
---
- Here executables can directly execute and access BIOS device drivers.
- There is no layer of protection in between.
- It does not have well defined structure.
- Such OS started as small, simple and limited system and grew beyond their original scope.
- example unx and MS-DOS
- It consist of two separable parts: Kernel and System Program
- Kernel is further separated into serious of interfaces and device drivers.
- The Kernel provides the file system, CPU scheduling, memory management and operating systems functions through system calls.
- System programs use the kernel supported system calls to provide useful functions like compilation and file manipulations.
- System call defines the program interface to UNIX.

Basic Input Output System (BIOS):
---
BIOS is the program of personal computer’s micro processor uses to get the PC started after you can turn it on.
It also manages control between Operating System and attached devices.

---
![[architecture.png|300]]

---
### Layered
- There are several layers between user and hardware.
- There is modularity in layer meaning each layer uses functions and services of only lower-level
- To provide proper H/W support, OS may be broken into smaller, more appropriate piece.
- The OS can then retain much greater control over the computer and the applications that make use of the computer.
- Implementations have more freedom to change the inner working of the system.
- Information hiding, leaving programmer free to implement low level routines as they see fit, provides that external interface of the routines remains unchanged.
- OS is divided into number of layers (Levels) each build on the top of the lower level.
- The Bottom Layer (Layer-0) is the Hardware Layer and highest layer (Layer-N) is the interface layer.
- An OS layer is implementations of an abstract object that is the encapsulation of data and operation that can manipulate those data.


# dual mode
- Protection is needed for the shared resources.
- At least two separate of mode of operation: User Mode and Monitor Mode (Also Called Kernel mode or Supervisor Mode) are needed.
    -  User Mode: Executing code has no ability to directly access H/W or reference memory.
    - Monitor Mode/Kernel mode/Supervisor Mode: Executing code has complete and unrestricted access to the underlying Hardware.
Mode bit
    - A bit called the mode bit is added to the H/W of the computer to indicate the current mode. User Mode : User(1) and Monitor Mode : Monitor(0)
    - Mode bit allow us to distinguish b/w an execution that is done on the behalf of the operating system and one that is done on behalf of the user.
- At system Boot Time, the H/W starts in monitor mode. The OS is then loaded and starts user processes in user mode.
- To execute programs in user mode it has to access the Kernal mode using system calls

System Protection
---
- Whenever a trap or interrupt occurs, the h/W switches from user mode to monitor mode/kernel mode.
- The dual mode of operation provides us with the means for protecting the OS from errant users and the errant’s users from one another.
- Privileged instructions (machine instructions which may cause harm) are executed only in monitor mode.
- The lack of H/W supported dual mode can cause serious shortcomings in the operating system

---
![[kernel.png|500]]



# Kernel

Kernel is central component of an operating system that manages operations of computer and hardware.
It basically manages operations of memory and CPU time.
Kernel loads first into memory when an operating system is loaded and remains into memory until operating system is shut down again.
It is responsible for various tasks such as disk management, task management, and memory management

There are many types of kernels that exists, but among them, the two most popular kernels are:
## types

Monolithic kernel
---
A monolithic kernel is a single code or block of the program.
It is a simplistic design which creates a distinct communication layer between the hardware and software.
It is one of types of kernel where all operating system services operate in kernel space.
It has dependencies between systems components
Most of the operations are performed by kernel via system call.

Microkernels
---
Microkernel manages all system resources.
In this type of kernel, services are implemented in different address space.
The user services are stored in user address space, and kernel services are stored under kernel address space.
So, it helps to reduce the size of both the kernel and operating system.
It has virtual memory and thread scheduling.
It is more stable with less services in kernel space. It puts rest in user space.

Reentrant Kernel
---
A reentrant kernel enables processes to give away the CPU while in kernel mode.
They do not hinder other processes from also entering in kernel mode.
A kernel that implement reentrant routines
Reentrant functions only modify local variable but do not alter global data structure.

---
![[microkernel.png|500]]



Differnces

|Basis|Mono|Micro|
|-|-|-|
|size|larger|smaller|
|execution|fast|slow|
|crash|whole system crashes|it does effects on working|
|code|less code|more code|
|example|Linux,OpenBDS|QNX,Symbian|



----

# System Structure
## Operating System Services
1. User Interface:
---
- Command Line Interface (CLI): It uses text command and method for entering them.
- Batch Interface: Commands and directives to control those commands are entered into files and those files are executed.
- Graphical User Interface (GUI): Interface with pointing device to direct I/O.
---
2. Program execution
---
system capability to load a program into memory and to run it.
Program must be able to ends its execution either normally and abnormally.
Program Loading -> Program Execution -> Program Termination

---
3. I/O operations
---
since user programs cannot execute I/O operations directly,
the operating System must provide some means to perform I/O operation either from file or I/O devices.

---
4. File-system manipulation
---
Many OS provides variety of file systems by which program is able to read, write, create, and delete files.

---
5. Communications
---
communication Implemented via shared memory or message passing.

---
6. Error detection
---
Ensure correct computing by detecting errors in the CPU (such as power failure) and memory hardware,
in I/O devices (such as connection failure), or in user programs.

---
7. Resource Allocation –
    - Many types of resources are managed by the operating system.
    - CPU cycle, main memory and file storage may have special allocation code.
    - I/O device may have much more general request and release code.
    - For example CPU scheduling routines that takes into account the speed of CPU.
    - There may also be routines to allot printers, modem, USB storage device and other peripheral device.
---
8. Protection and Security:
---
- Protection involves ensuring that all access to system resource is controlled.
- Security of the system from outside is also important.
- Security starts with each user having to authenticate himself to the system usually by means of password to allow the access to the resources.
---
9.  Accounting:-
---
- To keep track of which users and how much and what kind of computer resources.
- Used for accumulating usage statics.
- Usage statics may be valuable tool for the who wish to reconfigure the system to improve computing services.
- This record keeping may be for accounting (so that users be billed or simply for accumulating usage statistics.


### Operating System Design and Implementation
- Design and Implementation of an OS not “Solvable” but some approach have proven successful.
- Internal structure of different OS can vary widely.
- Start by defining goals and specifications.
- Affected by the choice of hardware and type of system.
- User goal and System goal :
    - User goal : OS should be convenient to use , easy to learn , reliable , state and fast.
    - System Goal: OS should be easy to design , implement and maintain as well as flexible , reliable , error free and efficient.
- Important principle to separate
    - Policy: What to be done.
    - Mechanism: How to do it.
- Mechanism determine how to do something, policies decide what to be done.
- Separation of policy from mechanism is very important principle, it allows maximum flexibility if policy decision are be changed later.


