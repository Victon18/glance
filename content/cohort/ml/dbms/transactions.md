# transaction processing
### transaction
A transaction is an action or series of actions.
It is performed usually by a single user to perform operations for accessing the contents of the database.
### operations on transaction
- Read (X)
----
Read operation is used to read the value of X from the database and stores it in a buffer in main memory.

- Write (X)
----
Write operation is used to write the value back to the database from the buffer.

- Commit
----
It is used to save the work done permanently.

- Rollback
---
It is used to undo the work done.

### transaction property
Property of Transaction are:
1. Atomicity
---
- It states that all operations of the transaction take place at once if not, the transaction is aborted.
- There is no midway, i.e., the transaction cannot occur partially.
- Each transaction is treated as one unit and either run to completion or is not executed at all.
- Atomicity involves the following two operations:
    - Abort: If a transaction aborts then all the changes made are not visible.
    - Commit: If a transaction commits then all the changes made are visible.

2. Consistency
---
- The integrity constraints are maintained so that the database is consistent before and after the transaction.
- The execution of a transaction will leave a database in either its prior stable state or a new stable state.
- The transaction is used to transform the database from one consistent state to another consistent state

3. Isolation
---
- It shows that the data which is used at the time of execution of a transaction cannot be used by the second transaction until the first one is completed.
- In isolation, if the transaction T1 is being executed and using the data item X, then that data item can't be accessed by any other transaction T2 until the transaction T1 ends.
- The concurrency control subsystem of the DBMS enforced the isolation property.

4. Durability
---
- The durability property is used to indicate the performance of the database's consistent state. It states that the transaction made the permanent changes.
- They cannot be lost by the system failure.
- When a transaction is completed, then the database reaches a state known as the consistent state.
- That consistent state cannot be lost, even in the event of a system's failure.
- The recovery subsystem of the DBMS has the responsibility of Durability property.

### state of transaction

1. Active state
---
- The active state is the first state of every transaction. In this state, the transaction is being executed.
- For example: Insertion or deletion or updating a record is done here.
- But all the records are still not saved to the database.

2. Partially committed
----
- In the partially committed state, a transaction executes its final operation, but the data is still not saved to the database.
- In the total mark calculation example, a final display of the total marks step is executed in this state.

3. Committed
----
- A transaction is said to be in a committed state if it executes all its operations successfully.
- In this state, all the effects are now permanently saved on the database system.

4. Failed state
-----
- If any of the checks made by the database recovery system fails, then the transaction is said to be in the failed state.
- In the example of total mark calculation, if the database is not able to fire a query to fetch the marks, then the transaction will fail to execute.

5. Aborted
----
- If any of the checks fail and the transaction has reached a failed state then the database recovery system will make sure that the database is in its previous consistent state.
- If not then it will abort or roll back the transaction to bring the database into a consistent state.
- If the transaction fails in the middle of the transaction then before executing the transaction, all the executed transactions are rolled back to its consistent state.
- After aborting the transaction, the database recovery module will select one of the two operations:
    - Re-start the transaction
    - Kill the transaction

![[state.png]]

## Concurrency transaction
In a particular transaction T1, most of the operations or instructions does not involve CPU.
Hence, to avoid CPU idle time, concurrent or parallel transaction are performed, So CPU can be utilized by other transaction

| T1       | State | T2       | state |
| -------- | ----- | -------- | ----- |
| Read(A)  | I/O   | -        | -     |
| A=A-100  | CPU   | Read(D)  | I/O   |
| Write(A) | I/O   | D=D-20   | CPU   |
| Commit() | -     | Write(D) | I/O   |
| -        | -     | Commit() | -     |

#### Advantages
1. Waiting time is reduced
---
Transaction does not have to wait so long

2. Resource utilisation is better
---
If one transaction is using CPU then other transaction uses I/O and vice versa
Hence resource utilisation is maximum

3. Response time is reduced
---
Less time is needed for compiling the transaction because the transaction does not have to wait so long to get the resource

4. Improved efficiency
---
many transaction are able to complete at a time

#### Problems
- Dirty Read Problem
----
It occurs when a transaction is reading the data that has been updated by another transaction which is still not committed


| T1       | State   | T2       | state      |
| -------- | ------- | -------- | ---------- |
| Read(A)  | A=100   | -        | -          |
| A=A+1    | A=101   | -        | -          |
| Write(A) | A=101   | -        | -          |
| -        | -       | R(A)     | dirty read |
| -        | -       | A=A+2    | -          |
| -        | -       | W(A)     | -          |
| -        | -       | commit() | -          |
| commit() | failure | -        | -          |

- Unrepeatable Read Problem
---
It occurs when Two or more read operation of the same transaction read different values of the same variable

| T1      | State | T2   | state |
| ------- | ----- | ---- | ----- |
| Read(A) | A=20  | -    | -     |
| -       | -     | R(A) | A=20  |
| A=A+2   | -     | -    | -     |
| W(A)    | A=22  | -    | -     |
| -       | -     | R(A) | A=22  |


- Phantom Read Problem
----
It occurs when a transaction reads a variable once but when it tries to read the same variable again, error occurs stating variable does not exist

| T1        | State     | T2      | state |
| --------- | --------- | ------- | ----- |
| Read(X)   | X=100     | -       | -     |
| -         | -         | Read(X) | X=100 |
| Delete(X) | Removed X | -       | -     |
| -         | -         | R(X)    | Error |

- Lost and Update Problem
----
It occurs due to update of the same record by two different transaction at the same time .
When two transaction are updating the same record at the same time in a DBMS then a lost update problem occurs.

| T1       | State          | T2       | state |
| -------- | -------------- | -------- | ----- |
| Read(X)  | X=50           | -        | -     |
| X=X+50   | X=100          | -        | -     |
| -        | -              | Read(X)  | x=50  |
| -        | -              | X=X+100  | X=150 |
| -        | -              | Write(A) | X=150 |
| Write(X) | update is lost | -        | -     |

## Concurrency Control Protocols

Timestamp Protocol
---
- also known as timestamp ordering protocol
- transactions are ordered based on their timestamp
- older transaction is given more priority
- Once timestamp is alloted it will not chanage throughtout transaction till it completes
- timestamp is unique for every transaction
- can be associated with
1. Transaction
    - for each transaction we give timestamp (system time) when transaction enters the system
    - If Tj enter the system after Ti; Ti is executed first before Tj
2. Data item
    - for each time item 'A', the protocol maintains two timesatmp; Read `[RTS(A)]` and Write `[WTS(A)]`
    - timestamp of data item is the timestamp of the transaction that last executed the data item A successfully.
- Allowed and rejected opeartions

<table border = '1px'>
<tr><th>Operation</th><th>Condition</th><th>Permission</th></tr>
<tr><th colspan = '3'>Ti request for Read(A)</th></tr>
<tr><td rowspan = '2'>R-W</td><td>TS(Ti) < WTS(A)</td><td>rejected and rollback</td></tr>
<tr><td>TS(Ti) >= WTS(A)</td><td>Allowed and the latest RTS(A) will be max</td></tr>
<tr><th colspan = '3'>Ti request for Write(A)</th></tr>
<tr><td rowspan = '2'>W-R</td><td>TS(Ti) < RTS(A)</td><td>rejected and rollback</td></tr>
<tr><td>TS(Ti) >= RTS(A)</td><td>Allowed and WTS(A) = max(TS(Ti),WTS(A))</td></tr>
<tr><td rowspan = '2'>W-W</td><td>TS(Ti) < WTS(A)</td><td>rejected and rollback</td></tr>
<tr><td>TS(Ti) >= WTS(A)</td><td>Allowed and WTS(A) = max(WTS(A),TS(Ti))</td></tr>
</table>

Note: A schedule following timestamp protocol is sure to be conflict serializable but not vice versa

Lock Based Protocol
----
- No transaction can perform read or write unless it acquires the appropriate lock on it.
- First it needs to acquire lock on data item then perform desired operation and then unlock it.

- Share Lock
---
- also called read lock
- used for readind data
- no updation can be performed
- denoted by Lock-S(A)

- Exclusive lock
---
- also called read-write lock
- use for read as well as write
- when an transaction is using exclusive lock on an item then no other transaction can use exclusive lock on same item till lock  is released.

2-Phase Locking Protcol (2PL)
----
- 2 Phase lock protocol that ensures the serializibility
- These two phases are :
1. Growing Phase
    - all the locks are issued and no locks are released
2. Shrinking Phase
    - all the changes are made to the data item and locks are released. Once in this phase no new locks can be acquired
- Adavntages:
    - always achieve serializibility
- Disadvantage:
    - may not be always reasonable
    - may suffer deadlocks
    - may suffer starvation
- Types of 2PL:
    1. Strict
        - a transaction is not allowed to release an exclusive lock until it has reached commit point.
        - It ensures recoverability of transaction in case of failure.
    2. Rigorous
        - a transaction is not allowed to release both exclusive and shared locks until it has reached commit point.
    3. Conservative
        - transaction are required to lock all items it needs before starting its execution.
        - If cannot lock at that time, then it waits till the item is available then lock all its item

Validation Based Protocol
----
Transaction has to go through these phases

1. Read phase
    - a transaction will read all the data items and store them in temporary variable (buffer).
    - Here  transactions are made to temporarily variable not in database.
2. validation phase
    - a validation test is performed to check if all changes made are valid or not. If valid then allowed for execution
3. Write phase
    - the changes that have passed the validation phase are executed to the actual database

now validation will be performed on the basis of timestamps associated with every transaction.
Theree timestamps are:
1. START(Ti): time when Ti starts execution
2. VALIDATION(Ti): time when Ti finishes its read phase and begins validation phase
3. FINISH(Ti): time when Ti started its write phase

The validation test
----
satisfy any one among three:
1. FINISH(Ti) < START(Tj): Tj is starting after Ti is finished
2. FINISH(Ti) < VALIDATE(Tj): Ti is already finished before Tj starts validation phase
3. VALIDATE(Ti) < VALIDATE(Tj): Ti has already validated before Tj validates.
