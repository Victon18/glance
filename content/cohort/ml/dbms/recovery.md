# Log Based Recovery
- The log is a sequence of records.
- Its use is to bring the database into last consistent state
- Log of each transaction is maintained in some stable storage so that if any failure occurs, then it can be recovered from there.
- Any operation which is performed on the database is recorded on the log.
- Prior to performing any modification to database, an update log record is created to reflect that modification.

# Types of Log Records
- `<Ti start>`: It contains information about when a transaction Ti starts.
- `<Ti, Xj, V1, V2> `: It contains information about when a transaction Ti updates its value.
- `<Ti,X>`: It contains information about when a transaction reads its value.
- `<Ti commit>`: It contains information about when a transaction Ti commits.
- `<Ti abort>`: It contains information about when a transaction Ti aborts.

# Log Record Representation
An update log record represented as:
`<Ti, Xj, V1, V2> ` has these fields:
1. <u>Transaction identifier</u>: Unique Identifier of the transaction that performed the write operation.
2. <u>Data item</u>: Unique identifier of the data item written.
3. <u>Old value</u>: Value of data item prior to write.
4. <u>New value</u>: Value of data item after write operation

Example
---
A = 1000
B = 2000
C = 700

| T1     | T2      | Log                |
| ------ | ------- | ------------------ |
| -      | -       | `[T1,start]`       |
| R(A)   | -       | `[T1,A]`           |
| A=A+50 | -       | `[T1,A,100,950]`   |
| W(A)   | -       | -                  |
| R(B)   | -       | `[T2,B]`           |
| B=B+50 | -       | `[T2,B,2000,2050]` |
| W(B)   | -       | -                  |
| -      | R(C)    | `[T2,C]`           |
| -      | C=C-100 | `[T2,C,700,600]`   |
| -      | W(C)    | -                  |
| -      | Commit  | `[T2,Commit]`      |

# Approaches to Modify Database
There are two approaches to modify the database:
1. Deferred database modification
-----
- The deferred modification technique occurs if the transaction does not modify the database until it has committed.
- In this method, all the logs are created and stored in the stable storage, and the database is updated when a transaction commits.
- Before reaching commit, all transaction updates are recorded in the local transaction workspace.
- If transaction fails before reaching commit operation, it will not have to  change the database in any way. So undo is not at all required.
- It may be necessary to Redo all the operation stored in local workspace . In short no-undo/redo algorithm
- Only new values are stored in logged

2. Immediate database modification:
-----
- The Immediate modification technique occurs if database modification occurs while the transaction is still active.
- In this technique, the database is modified immediately after every operation.
- All operations are recorded in the log in-order to enable recovery whenever needed
- If transaction fails before commit then the operation need to be undone, hence it record both undo and redo ie undo/redo algorithm
