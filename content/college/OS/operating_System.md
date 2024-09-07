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
# Kernal
Kernel is central component of an operating system that manages operations of computer and hardware.
It basically manages operations of memory and CPU time.
Kernel loads first into memory when an operating system is loaded and remains into memory until operating system is shut down again.
It is responsible for various tasks such as disk management, task management, and memory management

There are many types of kernels that exists, but among them, the two most popular kernels are:
## types

Monolithic kernel
---
A monolithic kernel is a single code or block of the program.
It provides all the required services offered by the operating system.
It is a simplistic design which creates a distinct communication layer between the hardware and software.
It is one of types of kernel where all operating system services operate in kernel space.
It has dependencies between systems components

Microkernels
---
Microkernel manages all system resources.
In this type of kernel, services are implemented in different address space.
The user services are stored in user address space, and kernel services are stored under kernel address space.
So, it helps to reduce the size of both the kernel and operating system.
It has virtual memory and thread scheduling.
It is more stable with less services in kernel space. It puts rest in user space.


## kernal mode vs user mode
- Inter-process communication
- Process synchronization
- Context switching

# Functions of OS
- Memory Management:- Allocation and De-allocation of memory
- Processor Management:- Keeps tracks of processor and status of process ie traffic controller.
- Device Management:- Keeps tracks of all devices ie I/O controller.
- File Management:- Keeps track of information, location, uses, status etc ie file system.
# Architetures of OS
### Simple
MS-DOS device drivers are collections of routines in memory that interact with hardware devices.
It provides the most functionality in least space.

- Disadvantages
---
Here executables can directly execute and access BIOS device drivers.
There is no layer of protection in between.
### Layered
- There are several layers between user and handware.
- There is modularity in layer meaning each layer uses functions and services of only lower-level


