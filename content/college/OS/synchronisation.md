# Interprocess Communication
- Concurrent access to shared data may result in data inconsistency
- Maintaining data consistency requires mechanisms to ensure the orderly execution of cooperating processes
- Processes within a system may be independent or cooperating
- Reasons for cooperating processes:
    - Information sharing
    - Computation speedup
    - Resources
    - Shared Code
    - Variables
- Two models of IPC
    1. Shared memory
    2. Message passing

Concurrent/Cooperating Process
---
- Two processes are said to be concurrent if they over lap in their execution
- Cooperating processes are processes that share resources.
- Cooperating process can affect or be affected by other processes, including sharing data
- Cooperating processes need interprocess communication (IPC)
---
Process Synchronization
---
- Process Synchronization is a way to coordinate processes that use shared data.
- It occurs in an operating system among cooperating processes.
- process synchronization helps to maintain shared data consistency and cooperating process execution.
- Processes have to be scheduled to ensure that concurrent access to shared data does not create inconsistencies.
---

# Race condition
Race condition
---
The situation where several processes access – and manipulate shared data concurrently.
The final value of the shared data depends upon which process finishes last

---
- Data inconsistency can result in what is called a race condition.
- It occurs when two or more operations are executed at the same time, not scheduled in the proper sequence, and not exited in the critical section correctly.
- To prevent race conditions, concurrent processes must be synchronized
Example

Consider this execution interleaving with “count = 5” initially:
	S0: producer execute register1 = count   {register1 = 5}
S1: producer execute register1 = register1 + 1   {register1 = 6}
S2: consumer execute register2 = count   {register2 = 5}
S3: consumer execute register2 = register2 - 1   {register2 = 4}
S4: producer execute count = register1   {count = 6 }
S5: consumer execute count = register2   {count = 4}

# Critical section problem
- Each process has critical section segment of code
- In critical section a process may be changing common variables, updating table, writing file, etc
- Critical section problem is to design protocol to solve this
- Critical section contains shared variables which need to be synchronized to maintain consistency of data variables
## solution

1. Mutual Exclusion:
----
If a process is executing in its critical section, then no other process is allowed to execute in the critical section.

2. Progress :
----
If no process is executing in the critical section and other processes are waiting outside the critical section,
then only those processes that are not executing in their remainder section can participate in deciding
which will enter in the critical section next, and the selection cannot be postponed indefinitely.

3. Bounded Waiting:
---
A bound must exist on the number of times that other processes are allowed to enter their critical sections
after a process has made a request to enter its critical section and before that request is granted

4. No Assumptions
---
No assumption related to hardware. Assume that each process executes at a nonzero speed
No assumption concerning relative speed of the N processes

# Peterson's solution
#### first solution
turn variable

|P0|P1|
|-|-|
|While(1){|While(1){|
|While(turn!=0);|While(turn!=1);|
|Critical Section|Critical Section|
|Turn = 1;|Turn = 0;|
|Remainder Section}|Remainder Section}|

#### second solution
flag variable

|P0|P1|
|-|-|
|While(1){|While(1){|
|`Flag[0]=True`|`Flag[1]=True`|
|`While (Flag[1]);`|`While (Flag[0]);`|
|Critical Section|Critical section|
|`Flag[0]=False;`|`Flag[1]=False;`|
|Remainder Section}|Remainder Section}|

#### third solution
turn variable
flag variable

|P0|P1|
|-|-|
|While(1){|While(1){|
|`Flag[0]=True`|`Flag[1]=True`|
|Turn=1;|Turn=0;|
|`While (turn==1&&Flag[1]);`|`While (turn==0&&Flag[0]);`|
|Critical Section|Critical section|
|`Flag[0]=False;`|`Flag[1]=False;`|
|Remainder Section}|Remainder Section}|

# Semaphore

