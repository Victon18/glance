# INTEGRITY CONSTRAINTS
- Integrity constraints are set of rules that helps ensure accuracy and consistency of data in the relational database.
- These constraints should never be violated.
- Some constraints are applied to table attributes and some to relationships between tables.
- Integrity constraints ensures that any changes or operations such as update, deletion, insertion that are made to the data in the database
do not result in loss of data consistency.
- Therefore, integrity constraints actually prevents any intentional and unintentional damage to the database.

# TYPES OF INTEGRITY CONSTRAINTS

1. DOMAIN CONSTRAINT
----
- Domain constraints defines the domain or the permitted set of values for a particular attribute.
- Following are the data type of domain: String, character, integer, time, date, number etc.
- The values of the attribute should match the domain specified for that attribute.

2. ENTITY INTEGRITY CONSTRAINT
---
- Entity integrity constraints states that the value of a primary key attribute should never be NULL
- Primary key uniquely identifies each tuple in a relation.
- Therefore if its value is null, then we wont be able to identify the records uniquely leading to data inconsistency

3. REFERENTIAL INTEGRITY CONSTRAINT
----
- Referential integrity constraints is specified between two tables: the referenced table(primary table) and the referencing table(related table)
- Referential integrity constraint is enforced when the foreign key of second table refers to the primary key of the first table.
- Therefore it ensure that every value of the foreign key in the second table should either be available in the primary key of the first table or it should be NULL.
Rules:
    - A record or tuple in the primary table cannot be deleted if a matching record exists in the related table.
    - The value of a primary key cannot be changed if that particular record has related records.
    - A value that does not exist in the primary key field of the primary table cannot be inserted in the foreign key field of the related table.
    - A NULL value can be inserted in the foreign key field if there are not matching record in the primary table.

4. KEY CONSTRAINT
----
- Key constraints specifies that all the values of a primary key in a relation must be unique and the value of the primary key must not be NULL.
- Primary key uniquely identifies each tuple in a relation.
- Therefore if its value is null, then we wont be able to identify the records uniquely leading to data inconsistency
