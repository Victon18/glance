SQL stands for Structured Query Language which is a standard language for accessing and manipulating databases.
SQL queries are categories into 4 types
    1. Data Query Language : Select
    2. Data Defination Language : Create Alter
    3. Data Manipulation Language : Insert Update
    4. Data Control Language : Grant Revoke

Table: A table is a database object which comprises rows and columns
Feild: A field provides specific information about the data in a table.
Record: Each individual entry in a table is called a record.

# creating database

```sql
CREATE DATABASE new;
/*for reserved keyword use*/
CREATE DATABASE [database1];
USE [database1];
```
# creating tabels

```sql
CREATE TABLE [customer personal details](
Cust_id int,
Cust_Name nvarchar(255),
Cust_no bigInt,
);
```
# droping tabels

```sql
DROP DATABASE [database1];
```
# datatypes

The data type of a column defines what value the column can hold

1. Binary
2. Charcter
    - char() -> 255 -> not changeable
    - varchar() -> 255 -> changeable
    - text -> 65,535
3. Numeric
    - integer or int or int4 -> 4 byte
    - smallint or int2 -> 2 byte
    - bigint or int8 -> 8 byte
    - serial -> 4 byte
    - smallserial -> 2 byte
    - bigserial -> 8 byte

3. Extract Numeric
4. String
5. Date
    - Date -> YYYY-MM-DD
    - Time -> HH:MM:SS
    - Year -> YYYY


# constraints
Rules for the data in a table can be specified using SQL constraints.
The kinds of data that can be entered into a table are restricted by constraints.
This validates the reliability and accuracy of the data in the table.

Types of constraints:
NOT NULL - prevents a column from having a NULL value.
UNIQUE - ensure that each value in a column is unique.
PRIMARY KEY - A combination of a NOT NULL and UNIQUE.
FOREIGN KEY - A field or column used to create a connection between two tables is known as a foreign key.
CHECK - check whether the values in a column satisfy a particular requirement.
DEFAULT - Sets a default value for a column in the absence of a value

```sql
CREATE TABLE Store_details (
  Store_ID int PRIMARY KEY,
  Store_Name varchar(200) NOT NULL,
  Sales int CHECK(Sales > 0),
  Order_no int UNIQUE,
  Store_Location varchar(200) DEFAULT 'Bangalore',
  City varchar(200),
  PersonID int,
  FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);
```
# insert into table
```sql
/*insert by values*/
INSERT INTO Store_details VALUES
(1,'Wallmart',2400,23,'Janpra','Madgoan',241309),
(2,'Flipkart',8600,245,'Ghanauti','Nandi',244567),
(3,'Citykart',700,4,'Delma',456788),
(4,'Trends',6700,35,'Astrik','Madgoan',324537),
(5,'Levi',3400,67,'Mahaballswar','Galgoti',7745);
/*insert by values and columns*/
Insert into store_details(Store, Store_name, Sales, Order_No, Store_Location, City, pincode) values
(11,'Jack and Jones',525,148,'Amblipura','Bangalore',560102);
Insert into store_details( Store, Store_name, Sales, City) values (12,'H&M',676,'Mumbai');
```

# alter table
```sql
/*add column*/
alter table store_details add profit int;
/*drop column*/
alter table store_details drop column profit

```
---
```sql
[db0].[[Costumer_details]]]
ALTER TABLE [table_name] ADD COLUMN column_name,[column_name];
ALTER TABLE [table_name] DROP COLUMN column_name,[column_name];
ALTER TABLE [table_name] DROP CONSTRAINT [constraint_name];
ALTER TABLE [table_name] ADD CONSTRAINT [constraint_name] UNIQUE (column_name);
SP_HELP [table_name];
SP_RENAME '[existing_table_name]','[new_table_name]';
SP_RENAME '[table_name].[existing_column_name]','new_column_name';
ALTER TABLE [table_name] ALTER COLUMN [column_name] VARCHAR (200) NOT NULL
```
# select
```sql
select Store_Name,Store_Location,City from Store_Details;
/*where clause and order by*/
SELECT * FROM orders
WHERE country IN ('US') OR state IN ('Marijuana','Goa')
ORDER BY country DESC;
```
---
```sql
SELECT * INTO column_name FROM table_name
UPDATE column_name SET ...;

SELECT * INTO order_copy FROM table_name
UPDATE oder_copy SET PROFIT=0, SALES=0, QUANTITY=0 WHERE COUNTRY='India';
```

# update table
```sql
/*where clause
----------------*/

update store_details set store_Name="Nike" Where City="Bangalore";

/*top clause
--------------------
The TOP Statement to limit the number of rows that are modified in an UPDATE statement.
When a TOP (n) clause is used with UPDATE, the update operation is performed on a random selection of 'n' number of rows*/

UPDATE top (5) store_details set sales = 100;

/*updating from another table
---------------------
another table with column name same datatype*/

UPDATE summary SET category = (SELECT order_No FROM store_details WHERE store_details.store = summary.store)
WHERE EXISTS (SELECT order_no FROM store_details WHERE store_details.store = summary.store);

/*Update top 10 records of table
-------------------------------------*/

alter table sales add Profit Varchar(5),Loss varchar(5)
set rowcount 10 update sales set Profit='YES',Loss='NO'
where Weekly_Sales>30000 SET ROWCOUNT 0;
select * from sales
```
# merging table
It is a combination of insert, delete and update statements.
If there is a Source table and a Target table that are to be merged,
then with the help of MERGE statement, all the three operations can be performed at once

```sql
/*Insert data using merge
---------------------------*/
MERGE TargetProducts AS Target
USING SourceTable AS Source
ON Source.ProductID = Target.ProductID
WHEN NOT MATCHED BY Target THEN
INSERT (ProductID,ProductName, Price)
VALUES (Source.ProductID,Source.ProductName, Source.Price);

/*Update
-------------*/
MERGE TargetProducts AS Target
USING SourceTable AS Source
ON Source.ProductID = Target.ProductID
WHEN MATCHED THEN UPDATE SET
Target.ProductName= Source.ProductName ,
Target.Price= Source.Price;

/*Delete
-----------------*/
MERGE TargetProducts AS Target
USING SourceTableAS Source
ON Source.ProductID = Target.ProductID
WHEN NOT MATCHED BY Source THEN DELETE;
```
# delete
It is used to delete existing records in a table

```sql
DELETE FROM store_details WHERE Sales=100;
```

# truncate
It is used to delete an existing data in a table , except the table itself

```sql
Truncate table store_details;
```

# drop
It is used to drop an existing table in a database

```sql
drop table store_details
```
# import data

# operators
## and operator
It is used to display record if all the conditions are separated by AND are TRUE
```sql
Select * from sales where Date='2010/08/13' and Dept=1
```
## or operator
It is used to display record if any of the conditions are separated by OR are TRUE
```sql
Select * from stores where Type='A' OR Size>100000
```
## not operator
It is used to display record if the specified condition in the query is FALSE, the SQL NOT operator will show the data.
```sql
Select * from stores where NOT Type ='A'
```
## Union operator
Union operator is used to combine the result set of two or more SELECT statement
```sql
Select * from stores where type='A' Union
Select * from Store_View where type='A' ORDER BY STORE
```
## Union All operator
Union All operator gives all rows from both tables including the duplicates
It is used to merge the result set of two or more SELECT statements.
It allows duplicate values.
```sql
Select * from stores where type='A' Union all
Select * from Store_View where type='A' ORDER BY STORE
```

## intersect
Intersect Operator helps to combine two select statements and returns the records which are common to both the select statements.
It is used to return only those entries that are present in both SELECT statements.
```sql
SELECT * FROM sales WHERE Weekly_Sales<1000 INTERSECT
SELECT * FROM Sales_View WHERE WEEKLY_SALES>800
```
## except
Except Operator combines two select statements and returns unique records from the left query which are not part of the right query.
EXCEPT returns only rows, which are not available in the second SELECT statement
```sql
SELECT * FROM sales EXCEPT SELECT * FROM SALES_VIEW;
```
## like
It is used to search a specified pattern in a column
`%` - Represents zero, one, or multiple characters
`_` - Represents a single character

```sql
SELECT Store, Dept, Weekly_Sales FROM sales WHERE Weekly_Sales LIKE'45%';
```
## between
It is used to select values within a given range
```sql
Select store temperature, fuel_price , cpi from features where cpi between 210 and 211;
```
# clause
## where
The WHERE clause is used to filter records
It is used to give some condition in SQL Query
```sql
Select * from sales where Date= '2010-08-13;
```
## group by
Group By is used to get an aggregate result with respect to a group.
It groups the selected rows based on identical values in a column or expression.
```sql
SELECT DEPT,AVG(WEEKLY_SALES) AS AVERAGE_SALES FROM SALES GROUP BY DEPT;
```
## order by
It is used to sort the result-set in ascending or descending order
```sql
select * from store_details order by store_name;
```
## having
Having clause is used in combination with Group By to impose conditions on groups.
The HAVING clause in SQL is utilized to filter the outcome set in view of aggregate functions like MIN() and MAX(), SUM() and AVG() and COUNT().
```sql
SELECT STORE,AVG(TEMPERATURE) AS AVG_TEMP FROM [dbo].[Features] GROUP BY
Store HAVING AVG(Temperature)>55

SELECT Distinct Store,Type, MAX(Size) FROM stores WHERE Store>5 group by
Store,Type having MAX(Size)> 50000 order by Store
```

# joins

By using joins, you can retrieve data from two or more tables based on logical relationships between the tables.
Types of Joins
1. INNER JOIN
2. FULL JOIN
3. LEFT JOIN
4. RIGHT JOIN
5. CROSS JOIN

## INNER JOIN
Inner Join returns records that have matching values in both tables.
It is also known as a simple join.
```sql
SELECT * FROM store1 INNER JOIN store2 ON store1.Store=Store2.Store WHERE Avg_WS>50000;
```

## LEFT JOIN
Left Join returns all the records from the left table and the matched records from the right table.

```sql
SELECT * FROM store1 LEFT JOIN store2 ON store1.Store=Store2.Store WHERE Avg_WS<50000;
```

## RIGHT JOIN
Right Join returns all the records from the right table and the matched records from the left table.

```sql
SELECT * FROM store1 RIGHT JOIN store2 ON store1.Store=Store2.Store WHERE Avg_WS<50000;
```

## FULL JOIN
It returns all rows from the LEFT table and the RIGHT table with NULL values in place where the join condition is not met.

```sql
SELECT Store2.Store, Store1.Avg_CPI, store1.Avg_Fuel_P, Store2.Avg_WS
FROM Store1 FULL OUTER JOIN store2 ON store1.Store=Store2.Store
WHERE Avg_WS BETWEEN 10000 AND 40000;
```
## JOINS USING GROUPBY AND HAVING CLAUSES
```sql
Select F.Store, S.Dept, AVG(S.Weekly_Sales) as Avg_WS
from Features F join Sales S on F.Store=S.Store
GROUP BY F.Store, S.Dept
HAVING AVG(S.Weekly_Sales)>10000
```

## JOINS USING GROUP BY AND ORDER BY CLAUSES
```sql
Select F.Store, AVG(S.Weekly_Sales) as Avg_WS
from Features F join Sales S on F.Store=S.Store
GROUP BY F.Store
ORDER BY Avg_WS DESC
```
# temporary table
Temporary Tables are most likely as Permanent Tables.
Temporary Tables are Created in TempDB and are automatically deleted as soon as the last connection is terminated.
Temporary tables are tables that exist temporarily on the SQL Server.
The temporary tables are useful for storing the immediate result sets that are accessed multiple times.
```sql
CREATE TABLE #Avg_F(Store INT, Avg_Temp DECIMAL(18,2),Avg_Fuel_P DECIMAL(18,2),Avg_CPI DECIMAL(18,2),Avg_UnEmp DECIMAL(18,2))
INSERT INTO #Avg_F(Store, Avg_Temp, Avg_Fuel_P, Avg_CPI, Avg_UnEmp)
SELECT Store,AVG(Temperature),AVG(Fuel_Price),AVG(CPI), AVG(Unemployment) FROM Features GROUP
BY Store having AVG(CPI)<150 order by Store SELECT * FROM #Avg_F
```

# Normalization and denoramalization

Normalization
----

Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity.
It involves structuring tables and their relationships according to certain rules (called normal forms)
to ensure that data is stored efficiently and without unnecessary duplication.

The main goals of normalization are:
1. Eliminate redundancy – Reduce duplicate data across tables.
2. Ensure data integrity – Maintain data consistency by dividing it into related tables.
3. Improve efficiency – Optimize updates, inserts, and deletes by reducing anomalies.

Normalization is generally achieved through a series of steps called normal forms:
1. 1NF (First Normal Form):
----
Ensure that each column contains atomic (indivisible) values, and each record is unique.

Example:
Consider a table that violates 1NF because it contains multiple values in a single column:
```sql
CREATE TABLE Orders ( OrderID INT, CustomerName VARCHAR(255),
Products VARCHAR(255) -- Multiple products in one column
);
INSERT INTO Orders (OrderID, CustomerName, Products) VALUES (1, 'John Doe', 'Laptop, Mouse');
/*To bring this table into 1NF, you would separate the products into individual rows:*/
CREATE TABLE Orders ( OrderID INT, CustomerName VARCHAR(255),
Product VARCHAR(255) -- One product per row
);
INSERT INTO Orders (OrderID, CustomerName, Product) VALUES (1, 'John Doe', 'Laptop'), (1, 'John Doe', 'Mouse');
```
2. 2NF (Second Normal Form):
----
Meet all the requirements of 1NF and
ensure that all non-key attributes are fully functionally dependent on the primary key.

Example:
Consider a table that violates 2NF because ProductName and Price are not dependent on CustomerID:
```sql
CREATE TABLE Orders (OrderID INT,
                    CustomerID INT,
                    CustomerName VARCHAR(255),
                    ProductID INT,
                    ProductName VARCHAR(255),
                    Price DECIMAL(10, 2) );
/*To normalize this to 2NF, you would split the table into two, ensuring that all non-key attributes are fully dependent on the primary key:*/
CREATE TABLE Customers ( CustomerID INT PRIMARY KEY, CustomerName VARCHAR(255) );
CREATE TABLE Products ( ProductID INT PRIMARY KEY, ProductName VARCHAR(255), Price DECIMAL(10, 2) );
CREATE TABLE Orders ( OrderID INT PRIMARY KEY, CustomerID INT, ProductID INT,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID),
FOREIGN KEY (ProductID) REFERENCES Products(ProductID) );
```

3. 3NF (Third Normal Form):
    Meet all the requirements of 2NF and ensure that all attributes are only dependent on the primary key (eliminate transitive dependency).
Example:
Consider a table that violates 3NF because ProductCategory depends on ProductName rather than directly on the primary key:
```sql
CREATE TABLE Orders ( OrderID INT PRIMARY KEY,
                        CustomerID INT,
                        ProductID INT,
                        ProductName VARCHAR(255),
                        ProductCategory VARCHAR(255));
/*To bring this table into 3NF, you would remove the transitive dependency by creating a new table:*/
CREATE TABLE Products ( ProductID INT PRIMARY KEY, ProductName VARCHAR(255), ProductCategory VARCHAR(255) );
CREATE TABLE Orders ( OrderID INT PRIMARY KEY, CustomerID INT, ProductID INT, FOREIGN KEY (ProductID) REFERENCES Products(ProductID) );
```
Use Cases:
Normalization is commonly used in transactional systems where data integrity and consistency are priorities.



Denormalization
---
Denormalization is the reverse process,
where normalized tables are combined to reduce the complexity of joins and improve read performance at the expense of some redundancy.
In denormalization, data is intentionally duplicated to speed up complex queries by avoiding the need for multiple joins between tables.

The main goals of denormalization are:
1. Improve query performance - Reduce the need for complex joins and improve data retrieval speed.
2. Simplify data structure – Combine related data into fewer tables to make queries more straightforward.
3. Enhance reporting capabilities – Some reporting systems work better with denormalized data for faster aggregation.

Denormalization is often used in big data systems or read-heavy applications where performance is more important than strict data consistency.

Use Cases:
Denormalization is common in data warehousing, analytical systems, or reporting, where query performance is more important than eliminating redundancy

