# creating database

```sql
CREATE DATABASE new;
/*for reserved keyword use*/
CREATE DATABASE [database1]
USE [database1]
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
DROP DATABASE [database1]
```
# constraints

```sql
CREATE TABLE Store_details (
  Store_ID int primary key,
  Store_Name varchar(200) not null,
  Sales int check(Sales > 0),
  Order_no int unique,
  Store_Location varchar(200) default 'Bangalore',
  City varchar(200),
  pincode int
);
```
```sql
INSERT INTO Store_details VALUES
(1,'Wallmart',2400,23,'Janpra','Madgoan',241309),
(2,'Flipkart',8600,245,'Ghanauti','Nandi',244567),
(3,'Citykart',700,4,'Delma',456788),
(4,'Trends',6700,35,'Astrik','Madgoan',324537),
(5,'Levi',3400,67,'Mahaballswar','Galgoti',7745);
```
# alter table
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
# update table
# import data
# select
```sql
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

