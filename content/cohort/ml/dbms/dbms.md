# database
database
---
A database is a collection of related data.

DBMS
---
A DBMS is a collection of inter-related data and a set of programs to access those data

DBMS Functions
---
- Defining:
---
a database involves specifying the data types, structures, and constraints for the data to be stored in the database.

- Constructing:
----
the database the process of storing data(inserting data) itself on some storage medium that is controlled by the DBMS.

- Manipulating:
----
a database includes querying (retrieving), updating (update/delete records) the database.

-  Sharing:
---
a database allows multiple users and programs to access the database concurrently.

# schema and instance
Similar to types and variables in programming languages

- Schema :
---
the logical structure of the database
    - the overall design of the database
    - Analogous to type information of a variable in a program
    - Physical schema: database design at the physical level
    - Logical schema: database design at the logical level

- Instance :
---
the actual content of the database at a particular point in time
Analogous to the value of a variable

# three schema architecture

- Physical level
---
    - Has an internal schema
    - Describes the physical storage structure of the database
    - Data structure used to store data
    - Access paths for database

- Conceptual level
---
    - What data stored in database
    - Relationship among those data
    - DBA uses this level
    - Hides details of physical storage structures

- External View or View level
---
    - Application programs
    - Describe part of the database that a particular user group is interested in
    - Hides rest of database from that user group
    - hide information (e.g., salary) for security purposes.

## Back-links
- Entity Relationship: [[ER]]
- Functional Dependency: [[FD]]
- Integrity Constant: [[IC]]
- Keys: [[key]]
- Normalization:  [[normalization]]
- Plsql: [[plsql]]
- Recovery of transaction failure: [[recovery]]
- Serializibility: [[serializibilty]]
- Transactions: [[transactions]]
- Deadlocks:[[deadlock]]
- [[dbms]]
