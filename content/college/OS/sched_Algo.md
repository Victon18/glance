# terminology
- **Arrival Time** -> time at which program came for execution
- **Burst Time** -> how long will the process run for
- **Finish Time** -> actual time process finished its task
- **Turn Araound Time** -> Finish Time - Arrival Time
- **waiting Time** -> Turn Around Time - Burst Time

#  FCFS scheduling algorithm
- FCFS -> Fist Come First Serve
- The process which arrives first in the ready queue is firstly assigned the CPU.
- In case of a tie, process with smaller process id is executed first.
- It is always non-preemptive in nature]

---
Advantage
- It is simple and easy to understand.
- It can be easily implemented using queue data structure.
- It does not lead to starvation.
---
Disadvantage
- It does not consider the priority or burst time of the processes.
- It suffers from convoy effect.

---
# convoy effect
- Consider processes with higher burst time arrived before the processes with smaller burst time.
- Then, smaller processes have to wait for a long time for longer processes to release the CPU.

# SJF
- SJF Scheduling can be used in both preemptive and non-preemptive mode.
- Non-Preemptive is called as **Shortest Job First (SJF)**
- Preemptive mode of Shortest Job First is called as **Shortest Remaining Time First (SRTF)**
## SJF scheduling algorithm
- SFJ -> Shortest Job First
- Out of all the available processes, CPU is assigned to the process having smallest burst time.
- In case of a tie, it is broken by FCFS Scheduling
## STRF
---
Advantages
- SRTF is optimal and guarantees the minimum average waiting time.
- It provides a standard for other algorithms since no other algorithm performs better than it
---
Disadvantages
- It can not be implemented practically since burst time of the processes can not be known in advance.
- It leads to starvation for processes with larger burst time.
- Priorities can not be set for the processes.
- Processes with larger burst time have poor response time.

---
# Priority
In Priority Scheduling,
    - Out of all the available processes, CPU is assigned to the process having the highest priority.
    -  In case of a tie, it is broken by FCFS Scheduling.
Priority scheduling are of two types
    - Non-preemptive mode
    - Preemptive mode

Advantages
    - It considers the priority of the processes and allows the important processes to run first.
    - Priority scheduling in preemptive mode is best suited for real time operating system.
 
Disadvantages
    - Processes with lesser priority may starve for CPU.
    - There is no idea of response time and waiting time.
Notes
    - The waiting time for the process having the highest priority will always be zero in preemptive mode.
    - The waiting time for the process having the highest priority may not be zero in non-preemptive mode. 
    - Priority scheduling in preemptive and non-preemptive mode behaves exactly same under following conditions
        -  The arrival time of all the processes is same
        -  All the processes become available
# Round robin

- Round Robin is a CPU scheduling algorithm where each process is assigned a fixed time slot in a cyclic way.
- It is simple, easy to implement, and starvation-free as all processes get fair share of CPU.
- It is preemptive as processes are assigned CPU only for a fixed slice of time at most.
- The disadvantage of it is more overhead of context switching. 
