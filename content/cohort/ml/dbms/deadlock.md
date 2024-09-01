# deadlock
### deadlock in DBMS
- In a database, a deadlock is an unwanted situation in which two or more transactions are waiting indefinitely for one another to give up locks
- It reduces resources utilization
- It drops the efficiency of the system

Properties that result in deadlock :
- Mutual Exclusion
- Hold and Wait
- No preemption
- circular Wait

![[deadlock.png|500]]

### deadlock Avoidance
Deadlock avoidance method is suitable for smaller databases
### deadlock detection
- In a database, when a transaction waits indefinitely to obtain a lock,
- then the DBMS should detect whether the transaction is involved in a deadlock or not.
- **Wait-for-graph** is one of the methods for detecting the deadlock situation.
----
- This method is suitable for smaller database.
- In this method a graph is drawn based on the transaction and their lock on the resource.
- If the graph created has a closed loop or a cycle, then there is a deadlock.
- It is denoted by `G(V,E)`; V are transactions, E are arrows showing which transaction is requesting from other transaction
### deadlock prevention
- Wait - Die Scheme (No preemption)
----
if a older transaction has locked data item and a younger transaction is waiting for it
then the younger transaction is killed (die) and restarted later with the same timestamp
- Wound - Wait Scheme
----
if a younger transaction has locked the item and an older data item is waiting for it,
older transaction kills the younger transaction and forcefully takes the item.
Then younger transaction waits till the older one frees the item.

- If the deadlock is detected then, a **recovery** is performed
- Deadlock prevention method is suitable for a large database.
- If the resources are allocated in such a way that deadlock never occurs, then the deadlock can be prevented.
- The DBMS analyzes the operations of the transaction whether they can create a deadlock situation or not.
- If they do, then the DBMS never allowed that transaction to be executed.
