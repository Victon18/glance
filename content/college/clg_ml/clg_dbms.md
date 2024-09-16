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

