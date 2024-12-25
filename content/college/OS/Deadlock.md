# Types of Resources
## Preemptable resouce
- It is one which can be allocated to a given process for a period of time,
- then be allocated to another process and then be reallocated to the first process without any ill effects.
- Examples of preemptable resources include:
    1. memory
    2. buffers
    3. CPU

## Non-preemptable resource
- It cannot be taken from one process and given to another without side effects.
- One obvious example is a printer

# Deadlock Conditions
1. Mutual exclusion
---
- only one resource can hold the critical section
---
2. Hold and wait
---
-  A process hold a resource and waits for another resource to execute
---
3. Non-preemptable
---
- when a process is holding a critical resource we cannot preemp until it completes
---
4. Circular wait
---
- process 1 holding resource that process 2 requires and vice-versa, forming a loop.
---
# Resource Allocation Graph
- Process is a circle
- Resource type is square
- Dots represent number of instances of resource in type.
- Request points to square, assignment comes from dot.
- If graph contains no loops then there isn't a deadlock.
- The request can be granted only if converting the request edge to an assignment, does not result in the formation of a loop.
## Nodes
- Single Instance
- Multiple Instance
## Edges
- request edge (Process -> Resource)
- assignment edge (Resource -> Process)
- claim edge (Process --> Resource)
# Handling deadlock
1. Prevention
---
- Prevent any of the 4 condition from happening
---
2. Avoidence
---
- Allow all deadlock condition but calculate cycles about to happen.
- We have prior knowledge of how resources will be requested
- Unsafe state -- A state that allows deadlocks to happen
- Safe state -- A state where deadlock will not happen
---
3. Detection
---
- Know that a deadlock has occured
---
4. Recovery
---
- Regain the resources
---
## safety algorithm (banker's)
- It is a safety algorithm used in deadlock avoidance in operating systems.
- It is designed to ensure that a system does not enter into an unsafe state
- It does so by analyzing resource allocation and requesting processes in real-time.

- The algorithm operates on the following principles:
    - It works with resources where each process has a maximum demand for resources, as well as a current allocation.
    - It uses the concept of a need matrix to calculate how many more resources each process might require to finish.
    - It checks whether there exists a sequence of processes that complete without causing a deadlock
- Banker's Algorithm Steps:
    1. Data Structures:
        - Available[]: Available resources of each type.
        - Max[][]: Maximum demand of each process for each resource type.
        - Allocation[][]: Current allocation of resources to each process.
        - Need[][]: Resources needed by each process to complete (calculated as Need[i][j] = Max[i][j] - Allocation[i][j]).
    2. Safety Check:
        - The requested resources are less than or equal to the Available[] resources.
        - If yes, assume the request is granted and update the available resources and allocation.
        - Then, check if the system remains in a safe state after the allocation.
        - If it's safe, the request is granted; otherwise, it's denied.
    3. Safe State Check:
        - if there exists a sequence of processes such that each process can finish with the available resources,
        - including those released by previously completed processes.

# Deadlock recovery
## PROCESS TERMINATION:
- Could delete all the processes in the deadlock -- this is expensive.
- Delete one at a time until deadlock is broken ( time consuming ).
- Select who to terminate based on priority, time executed, time to completion, needs for completion, or depth of rollback
## RESOURCE PREEMPTION:
- Select a victim - which process and which resource to preempt.
- Rollback to previously defined "safe" state.
- Prevent one process from always being the one preempted ( starvation ). 

















- Numerical Example of Banker's Algorithm:

<table style="table-layout: auto;">
    <tr><td>Process</td><td colspan="3">Maximum</td><td colspan="3">Allocation</td>
    <td colspan="3">Need</td><td colspan="3">Available</td></tr>
    <tr><td>P1</td><td >A</td><td>B</td><td>C</td><td>A</td><td>B</td><td>C</td>
     <tr><td>P1</td><td >A</td><td>B</td><td>C</td><td>A</td><td>B</td><td>C</td>
    <F8><td>A</td><td>B</td><td>C</td><td>A</td><td>B</td><td>C</td></tr>
   <td>A</td><td>B</td><td>C</td><td>A</td><td>B</td><td>C</td></tr>
    <tr><td>P1</td><td >A</td><td>B</td><td>C</td><td>A</td><td>B</td><td>C</td>
    <td>A</td><td>B</td><td>C</td><td>A</td><td>B</td><td>C</td></tr>



</table>


Available Resources:
Resource	A	B	C
Available	3	3	2
Maximum Demand (Max):
Process	A	B	C
P0	7	5	3
P1	3	2	2
P2	9	0	2
Current Allocation (Allocation):
Process	A	B	C
P0	2	1	1
P1	1	2	1
P2	3	3	2
Need (Need = Max - Allocation):
Process	A	B	C
P0	5	4	2
P1	2	0	1
P2	6	0	0
Request by Process P1:

Let's say P1 requests 1 unit of A, 0 units of B, and 2 units of C. We need to check whether granting this request would put the system in an unsafe state.
Step-by-Step Execution:
1. Check if the request is less than or equal to Available:

    P1 requests 1 unit of A, 0 units of B, and 2 units of C.
    Available[] = [3, 3, 2].
    Since the requested resources (1, 0, 2) are less than or equal to the available resources (3, 3, 2), the request can potentially be granted.

2. Pretend to allocate resources:

Assume the request is granted:

    Update Available[]:
    New Available = [3-1, 3-0, 2-2] = [2, 3, 0].
    Update Allocation[][]:
    New Allocation for P1 = [1+1, 2+0, 1+2] = [2, 2, 3].
    Update Need[][]:
    New Need for P1 = [3-2, 2-2, 2-3] = [1, 0, 0].

3. Check if the system is in a safe state:

    We need to find if there is a sequence of processes that can complete with the current available resources.
    New Available[] = [2, 3, 0].

Now, we check if any process can finish with the available resources:

    P0's Need = [5, 4, 2]. P0 can't finish because it needs more resources than are available.

    P1's Need = [1, 0, 0]. P1 can finish because its needs (1, 0, 0) are less than or equal to the available resources (2, 3, 0).

    If P1 finishes, it will release its resources: [2, 2, 3]. Now, update Available[]:
        New Available = [2+2, 3+2, 0+3] = [4, 5, 3].

    P0's Need = [5, 4, 2]. Now that P1 has finished, Available = [4, 5, 3], so P0 can also finish (it needs 5, 4, 2), and will release its resources: [2, 1, 1].
        New Available = [4+2, 5+1, 3+1] = [6, 6, 4].

    P2's Need = [6, 0, 0]. Now P2 can also finish (it needs 6, 0, 0), and will release its resources: [3, 3, 2].
        New Available = [6+3, 6+3, 4+2] = [9, 9, 6].

Since there is a safe sequence (P1 → P0 → P2), the system remains in a safe state, and the request by P1 is granted.
Conclusion:

The Banker's algorithm checks resource allocation requests and ensures that the system stays in a safe state by simulating the allocation and checking for a safe sequence of process execution. In this example, the request by P1 was granted because it did not lead to an unsafe state.
You said:
can you give me numerical example of detection algorithm as well
ChatGPT said:
ChatGPT

Certainly! A detection algorithm typically identifies issues such as deadlocks or other resource allocation problems after they occur. One common algorithm for detecting deadlocks is the Resource Allocation Graph (RAG) algorithm, which is used to represent resource allocation and can be used to detect deadlocks in a system.

I'll explain a deadlock detection algorithm using the Resource Allocation Graph (RAG) approach with a numerical example.
Deadlock Detection Using the Resource Allocation Graph (RAG) Algorithm

In this approach, we represent the system as a graph where:

    Processes are represented by nodes.
    Resources are also represented by nodes.
    Edges are used to indicate relationships:
        Request edges from a process to a resource (P → R) indicate that a process is requesting a resource.
        Assignment edges from a resource to a process (R → P) indicate that a resource is assigned to a process.

A deadlock occurs if there is a cycle in the graph (i.e., a process is waiting for a resource that is held by another process, forming a circular chain).
Numerical Example of Deadlock Detection
Scenario:

    We have 3 processes (P1, P2, P3) and 3 resources (R1, R2, R3).
    Each process has certain resources assigned and requests additional resources.

Step 1: Define the system resources and allocations

    Available resources:
        R1 = 1
        R2 = 2
        R3 = 1

    Resource Allocation (which resources are currently held by processes):
        P1 holds: R1 (1 unit)
        P2 holds: R2 (1 unit)
        P3 holds: R2 (1 unit)

    Resource Request (which resources are requested by processes):
        P1 requests: R2 (1 unit)
        P2 requests: R3 (1 unit)
        P3 requests: R1 (1 unit)

Step 2: Construct the Resource Allocation Graph (RAG)

    Nodes:
        Processes: P1, P2, P3.
        Resources: R1, R2, R3.

    Edges:
        Request edges: These represent requests made by processes for resources.
            P1 → R2 (P1 requests R2)
            P2 → R3 (P2 requests R3)
            P3 → R1 (P3 requests R1)
        Assignment edges: These represent resources assigned to processes.
            R1 → P1 (R1 is assigned to P1)
            R2 → P2 (R2 is assigned to P2)
            R2 → P3 (R2 is assigned to P3)

The resulting Resource Allocation Graph (RAG) looks like this:

       R1    R2    R3
        ↑     ↑     ↑
       P1 ←─ P2 ←─ P3
        ↑     ↑     ↑

Step 3: Check for cycles in the graph

    In this graph, we have the following relationships:
        P1 is holding R1 and is requesting R2.
        P2 is holding R2 and is requesting R3.
        P3 is holding R2 and is requesting R1.

Now, let's check for cycles:

    Starting at P1:
        P1 → R2 (P1 requests R2)
        R2 → P2 (R2 is assigned to P2)
        P2 → R3 (P2 requests R3)
        R3 → P3 (R3 is assigned to P3)
        P3 → R1 (P3 requests R1)
        R1 → P1 (R1 is assigned to P1)

This forms a cycle: P1 → R2 → P2 → R3 → P3 → R1 → P1.

Since there is a cycle, this indicates a deadlock in the system. The processes P1, P2, and P3 are in a circular wait, each waiting for a resource held by another, and no process can proceed.
Conclusion of the Detection Algorithm:

    The Resource Allocation Graph (RAG) has a cycle, which indicates that there is a deadlock in the system.
    In this case, processes P1, P2, and P3 are deadlocked because they are each waiting for a resource held by another, forming a circular wait.

Step 4: Resolving the Deadlock

Once a deadlock is detected, the system can take steps to resolve it, such as:

    Terminating one or more processes to break the cycle.
    Preempting resources from one process and allocating them to another.

Summary of the Deadlock Detection Algorithm:

    The Resource Allocation Graph (RAG) is a graphical method to detect deadlocks by searching for cycles.
    A cycle in the graph indicates a deadlock situation.
    If no cycle exists, the system is not deadlocked and is in a safe state.

In the above example, the presence of a cycle in the RAG confirms that a deadlock has occurred.



