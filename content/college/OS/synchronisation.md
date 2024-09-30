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

| P0                 | P1                 |
| ------------------ | ------------------ |
| While(1){          | While(1){          |
| While(turn!=0);    | While(turn!=1);    |
| Critical Section   | Critical Section   |
| Turn = 1;          | Turn = 0;          |
| Remainder Section} | Remainder Section} |

Dry runs
```C
int turn=0;
//process 1
while(1){
    while(turn!=0){}//false
    //Critical Section
    turn = 1; //turn=1
}
// process 2
while(1){
    while(turn!=1){}//false
    //Critical Section
    turn = 0; //turn=0
}
```
It follows mutual exclusion but not progress
ie process 2 is not participating
```C
int turn=0;//turn = 1
//process 1
while(1){
    while(turn!=0){}//1.false //2.true(not able to access CS)
    //Critical Section
    turn = 1; //turn=1
}
```
#### second solution
flag variable

| P0                 | P1                 |
| ------------------ | ------------------ |
| While(1){          | While(1){          |
| `Flag[0]=True`     | `Flag[1]=True`     |
| `While (Flag[1]);` | `While (Flag[0]);` |
| Critical Section   | Critical section   |
| `Flag[0]=False;`   | `Flag[1]=False;`   |
| Remainder Section} | Remainder Section} |

Dry runs
```C
int Flag[] = {false,false};
//process 1
while(1){
    flag[0]=true;//flag[ture,false]
    while(flag[1]){}//false
        //Critical Section
    flag[0]=false; //flag[false,false]
}
// process 2
while(1){
    flag[1] = true;//flag[false,true]
    while(flag[0]){}//false
        //Critical Section
    flag[1]=false; //flag[false,false]
}
```
It follows mutual exclusion
```C
while(1){
    flag[0]=true;//flag[ture,false]
    while(flag[1]){}//false
        //Critical Section
    flag[0]=false; //flag[false,false]
}
```
It follows progress as well
but there exists a deadlock
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

Dry runs
```C
int turn = 0;
int Flag[] = {false,false};
//process 1
while(1){
    flag[0]=true;//flag[ture,false]
    turn = 1; // turn = 1
    while(turn==1&&flag[1]){}//false
        //Critical Section
    flag[0]=false; //flag[false,false]
}
// process 2
while(1){
    flag[1] = true;//flag[false,true]
    turn = 0; //turn = 0
    while(turn==0&&flag[0]){}//false
        //Critical Section
    flag[1]=false; //flag[false,false]
}
```
It follows mutual exclusion
```C
while(1){
    flag[0]=true;//flag[ture,false]
    turn = 1; // turn = 1
    while(turn==1&&flag[1]){}//false
        //Critical Section
    flag[0]=false; //flag[false,false]
}

```
It follows progress as well and there is no deadlock condition
But these work for only two solution
# Semaphore
- this solution works for n number of concurrent program
- Semaphore is simply an integer variable which is non-negative and shared between threads
- This variable is used for critical section in the multiprocessing environment.
- It uses two basic function wait(S) and Signal(S).

| Wait         | Signal     |
| ------------ | ---------- |
| wait(S):     | signal(S): |
| while(S<=0): | S++;       |
| S--;         | --         |

Shared data:
	   semaphore mutex;
        mutex = 1; (Initially)
Process Pi:
```C
do {
    wait(mutex);
    //critical section
 	signal(mutex);
    //remainder section
} while (1);
```

## Two Types of Semaphores

- Binary Semaphore
---
This is also known as mutex lock.
It can have only two values –> 0 and 1.
Its value is initialized to 1.
It is used to implement the solution of critical section problem with multiple processes.

---
- Counting Semaphore
---
Its value can range over an unrestricted domain.
It is used to control access to a resource that has multiple instances
Can implement a counting semaphore S as a binary semaphore.

---
## Classic problem

#### Producer Consumer with Bounded-Buffer Problem
---
- We have a buffer of fixed size.
- A producer can produce an item and can place in the buffer.
- A consumer can pick items and can consume them.
- We need to ensure that when a producer is placing an item in the buffer,
    then at the same time consumer should not consume any item.
- In this problem, buffer is the critical section.
- To solve this problem, two counting semaphores – Full and Empty.
- “Full” keeps track of number of items in the buffer at any given time
- “Empty” keeps track of number of unoccupied slots.


Shared data : semaphore full, empty, mutex;
Initially:  full = 0, empty = n, mutex = 1

| Writing             | Reading                    |
| ------------------- | -------------------------- |
| do{                 | do{                        |
| produce an item     | wait(full);                |
| wait(empty);        | wait(mutex);               |
| wait(mutex);        | remove an item from buffer |
| add nextp to buffer | signal(mutex);             |
| signal(empty);      | Signal(empty);             |
| signal(mutex);      | consume item in nextc      |
| }while(1);          | }while(1);                 |

---
#### Readers and Writers Problem
anyone can read value even in critical section
But no-one can write when someone is writing

semaphore mutex, write;
Initially mutex = 1, write = 1, read-count = 0

| Write          | Read               |
| -------------- | ------------------ |
| wait(write);   | wait(mutex):       |
| writing..      | readcount++;       |
| signal(write); | if (readcount==1)  |
| -              | wait(write);       |
| -              | signal(mutex);     |
| -              | reading...         |
| -              | wait(mutex);       |
| -              | readcount--;       |
| -              | if (readcount==0): |
| -              | signal(write);     |
| -              | signal(read);      |

---
#### Dining-Philosophers Problem
Shared data
		semaphore `chopstick[5]`;
Initially all values are 1

```C
do {
    wait(chopstick[i]);
    wait(chopstick[(i+1) % 5]);

	#eat

	signal(chopstick[i]);
	signal(chopstick[(i+1) % 5]);

    #think

	} while (1);
```
