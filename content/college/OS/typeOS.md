

# types of OS

1. Batch Operating System
---
This type of operating system does not interact with the computer directly.
There is an operator which takes similar jobs having the same requirements and groups them into batches.
It is the responsibility of the operator to sort jobs with similar needs.
Batch Operating System is designed to manage and execute a large number of jobs efficiently by processing them in groups.

Advantages of Batch Operating System
    - Multiple users can share the batch systems.
    - The idle time for the batch system is very less.
    - It is easy to manage large work repeatedly in batch systems.

Disadvantages of Batch Operating System
    - Batch systems are hard to debug.
    - It is sometimes costly.
    - The other jobs will have to wait for an unknown time if any job fails.
    - The processing time for jobs is commonly difficult to accurately predict while they are in the queue.

Examples of Batch Operating Systems: Payroll Systems, Bank Statements, etc.

---
2. Multi-Programming Operating System
---
In this more than one program is present in the main memory and any one of them can be kept in execution.
This is basically used for better utilization of resources.

Advantages of Multi-Programming Operating System
    - Multi Programming increases the Throughput of the System.
    - It helps in reducing the response time.

Disadvantages of Multi-Programming Operating System
    - There is not any facility for user interaction of system resources with the system.

---
3. Multi-Processing Operating System
---
It is a type of Operating System in which more than one CPU is used for the execution of resources.
It betters the throughput of the System.

Advantages of Multi-Processing Operating System
    - It increases the throughput of the system.
    - As it has several processors, so, if one processor fails, we can proceed with another processor.

Disadvantages of Multi-Processing Operating System
    - Due to the multiple CPU, it can be more complex and somehow difficult to understand.

---
4. Multi-Tasking Operating System
---
It is a multiprogramming Operating System with having facility of a Round-Robin Scheduling Algorithm.
It can run multiple programs simultaneously.

There are two types of Multi-Tasking Systems which are listed below.
    - Preemptive Multi-Tasking
    - Cooperative Multi-Tasking

Advantages of Multi-Tasking Operating System
    - Multiple Programs can be executed simultaneously in Multi-Tasking Operating System.
    - It comes with proper memory management.

Disadvantages of Multi-Tasking Operating System
    - The system gets heated in case of heavy programs multiple times.

---
5. Time-Sharing Operating Systems
---
- Each task is given some time to execute so that all the tasks work smoothly.
- Each user gets the time of the CPU as they use a single system.
- These systems are also known as Multitasking Systems.
- The task can be from a single user or different users also.
- The time that each task gets to execute is called quantum.
- After this time interval is over OS switches over to the next task.

Advantages of Time-Sharing OS
    - Each task gets an equal opportunity.
    - Fewer chances of duplication of software.
    - CPU idle time can be reduced.
    - Resource Sharing:
        Time-sharing systems allow multiple users to share hardware resources
    - Improved Productivity:
        Time-sharing allows users to work concurrently, thereby reducing the waiting time.
    - Improved User Experience:
        Time-sharing provides an interactive environment that allows users to communicate with the computer

Disadvantages of Time-Sharing OS
    - Reliability problem.
    - One must have to take care of the security and integrity of user programs and data.
    - Data communication problem.
    - High Overhead:
        They have a higher overhead due to the need for scheduling, context switching.
    - Complexity:
        Time-sharing systems are complex and require advanced software to manage multiple users simultaneously.
    - Security Risks:
        With multiple users sharing resources, the risk of security breaches increases.

Examples of Time-Sharing OS with explanation
    IBM VM/CMS,  TSO (Time Sharing Option), Windows Terminal Services

---
6. Distributed Operating System
---
- Various autonomous interconnected computers communicate with each other using a shared communication network.
- Independent systems possess their own memory unit and CPU.
- These are referred to as loosely coupled systems or distributed systems .
- Remote access of files is enabled within the devices connected in that network.

Advantages of Distributed Operating System
    - Failure of one will not affect the other network communication, as all systems are independent of each other.
    - Electronic mail increases the data exchange speed.
    - Since resources are being shared, computation is highly fast and durable.
    - Load on host computer reduces.
    - These systems are easily scalable as many systems can be easily added to the network.
    - Delay in data processing reduces.

Disadvantages of Distributed Operating System
    - Failure of the main network will stop the entire communication.
    - To establish distributed systems the language is used not well-defined yet.
    - These types of systems are not readily available as they are very expensive.
        Not only that the underlying software is highly complex and not understood well yet.

Examples of Distributed Operating Systems are LOCUS, etc.

Issues With Distributed Operating Systems
    - Networking causes delays in the transfer of data between nodes of a distributed system.
    - Control functions like scheduling, resource allocation, and deadlock detection have to be performed in several nodes
    - Messages exchanged by processes present in different nodes may travel over public networks

---
7. Network Operating System
---
- These systems run on a server
- provide the capability to manage data, users, groups, security, applications, and other networking functions.
- allow shared access to files, printers, security, applications, and other networking functions over a small private network.
- popularly known as tightly coupled systems .

Advantages of Network Operating System
    - Highly stable centralized servers.
    - Security concerns are handled through servers.
    - New technologies and hardware up-gradation are easily integrated into the system.
    - Server access is possible remotely from different locations and types of systems.

Disadvantages of Network Operating System
    - Servers are costly.
    - User has to depend on a central location for most operations.
    - Maintenance and updates are required regularly.

Examples
Microsoft Windows Server 2003, Microsoft Windows Server 2008, UNIX, Linux, Mac OS X, Novell NetWare, BSD, etc.

---
8. Real-Time Operating System
---
- These types of OSs serve real-time systems.
- The time interval required to process and respond to inputs is very small.
- This time interval is called response time.
- Real-time systems are used when there are time requirements that are very strict like missile systems,  air traffic control systems, robots, etc.

Types of Real-Time Operating Systems
    - Hard Real-Time Systems
    - Soft Real-Time Systems

Advantages of RTOS
    - Maximum Consumption: Maximum utilization of devices and systems, thus more output from all the resources.
    - Task Shifting: The time assigned for shifting tasks in these systems is very less.
    - Focus on Application: Focus on running applications and less importance on applications that are in the queue.
    - Error Free: These types of systems are error-free.
    - Memory Allocation: Memory allocation is best managed in these types of systems.

Disadvantages of RTOS
    - Limited Tasks: Very few tasks run at the same time.
    - Use heavy system resources: Sometimes the system resources are not so good and they are expensive as well.
    - Complex Algorithms: The algorithms are very complex and difficult for the designer to write on.
    - Device driver and interrupt signals: It needs specific device drivers and interrupts signal to respond earliest to interrupts.
    - Thread Priority: It is not good to set thread priority as these systems are very less prone to switching tasks.

Examples Scientific experiments, medical imaging systems, industrial control systems, etc.



