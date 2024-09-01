# keys
1. Primary Key
----
- A Primary Key is an attribute or minimum set of attributes through which we can determine entire table uniquely.
- Not null and uinque
- only one can exist

2. Candidate Key or Secondary Key
----
- Candidate Keys are those attributes that uniquely identify rows of a table.
- The PK of a table is selected from one of the Candidate Keys. Same properties as pk
- more than one

3. Alternate Key
----
- all the keys which did not become the Primary Key are called Alternate Keys.

4. Super Key
----
- all those columns of a table than capable of identifying the other columns of that table uniquely will all be considered super keys.
- Super Key is the superset of a Candidate Key

5. Composite Key
---
- Composite Key is a set of two or more attributes that help identify each tuple in a table uniquely.
- when taken all together, they will ensure uniqueness

6. Unique Key
----
- A Unique Key differs from a PK because it can have only one null value, whereas a PK cannot have any null values.
- Unique Key is a column or set of columns that uniquely identify each record in a table.

7. Surrogate Key or Artificial Key
---
- it is created when we don’t have any natural PK.
- Surrogate keys in SQL are allowed when:
  No property has the parameter of the Primary Key.
  In the table when the Primary Key is too big or complicated

8. Foreign Key
---
- Foreign Key is used to establish relationships between two tables.
- A Foreign Key will require each value in a column or set of columns to match the Primary Key of the referential table.

9. Partial Key
----
- The set of attributes that are used to uniquely identify a weak entity set is called the Partial key.
- The Partial Key of the weak entity set is also known as a discriminator.


