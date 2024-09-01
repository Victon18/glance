Database driver
----
 A database driver is a software component that provides an interface between the
Python program and the database management system.
There are several popular Python libraries for database connectivity,
including mysql-connector-python.

Procedure
---

- Step1: Import necessary module
---
```python
import mysql.connector
```
- Step2: Establish a connection between python program and database
---
The connect() function takes several parameters, including the hostname, username, password, and database name.
Create a connection object.

```python
mydb = mysql.connector.connect(
    host = "localhost"
    username = "root"
    password = "Aon@SQl123"
    database = "University"
)
```
- STEP 3: Create a cursor object
---
A cursor object acts as a pointer to a specific location in the database, allowing you to retrieve, insert, update, or delete data.
```python
mycursor = mydb.cursor()
```
- STEP 4: Execute SQL Commands
---
After the cursor object is created above, we can execute an SQL query using the execute() method on the cursor object.
```python
# creating database
mycursor.execute("CREATE DATABASE UNIVERSITY")
# check successful creation of databse
mycursor.execute("SHOW DATABASES")
for x in mycursor:
    print(x)
# can also use instead of for loop
print(mycursor.fetchall()
# creating table
mycursor.execute("CREATE TABLE Employees (emp_name VARCHAR(255), address VARCHAR(255))")
# checking execution
mycursor.execute("SHOW TABELS")
for x in mycursor:
    print(x)
# inserting data
mycursor.execute("CREATE INTO Employees VALUES('Alka','Uttar Pradesh')")
# checking execution
mycursor.execute("SELECT * FROM Employees")
for x in mycursor:
    print(x)
```

- STEP 5: Commit Changes and Close the Connection
---
```python
mydb.commit()
mycursor.close()
mydb.close()
```


Handling errors and Exceptions
---
Handling errors and exceptions is an important part of writing reliable code in programming.
It is important to handle errors and exceptions in your code to make it more reliable and to prevent unexpected crashes or behavior.
To do this, we use try-except blocks in order to catch any errors at different stages of the code.
If an error occurs, a message is printed and exited from the program.

```python
try:
    mydb = mysql.connector.connect(
    host = "localhost"
    username = "root"
    password = "Aon@SQl123"
    database = "University"
    )
except mysql.connector.Error as err:
    print("Error connecting to database",err)
    exit()
```

Different methods used for database programming
----
These methods are fundamental for Python database programming using libraries and database connectors
You can try executing these:
- connect(): Establishes a connection to the database.
- cursor(): Creates a cursor object which allows executing SQL commands.
- execute(): Executes a SQL query or command.
- executescript(): Executes multiple SQL statements separated by semicolons.
- executemany(): Executes the same SQL statement with multiple sets of parameters.
- commit(): Saves changes made to the database since the last commit.
- rollback(): Rolls back any changes made since the last commit.
- fetchone(): Retrieves the next row of a query result set, returning a single tuple.
- fetchall(): Retrieves all rows of a query result set, returning a list of tuples.
- fetchmany(n): Retrieves the next 'n' rows of a query result set, returning a list of tuples.
- close(): Closes the cursor and the database connection.

Cursor attributes: (cursor functions)
---

1. Description
---
The description attribute provides metadata about the columns in the result set, such as column names, data types, and sizes.

```python
mycursor.execute("SELECT * FROM Employees")
# Accessing descrption atttribute
print("Description attribute:")
print(mycursor.description)
```
2. Rowcount
---
Indicates the number of rows that were affected by the last operation executed by the cursor.
This is particularly useful for operations like INSERT, UPDATE, DELETE, etc.

```python
mycursor.execute("INSERT INTO Employees VALUES('Amy','Russia')")
# Accessing rowcount atttribute
print("\nRowcount attribute:")
print("Number of rows affected:",mycursor.rowcount)
```

3. Current Row Position
---
Indicates the current position of the cursor within the result set.
This can be useful for iterating through the result set or for determining the position of a particular row.

```python
mycursor.execute("INSERT INTO Employees VALUES('Amy','Russia')")
# Accessing current row  atttribute
print("\nCurrent row  position:")
for row in mycursor:
    print(row)
    print("Current row position: ",mycursor.rowcount)
```

Stored Procedures and Stored functions:
------
- Stored procedure and Stored Function, both can be defined as a set of logically written statements, stored in the database and are executed when called, to perform a specific task.
- Both function as well as procedure have a unique named block of code which is compiled and stored in the database.
- Any stored procedure or function created, remains useless unless it is called. Therefore, after creating a stored procedure or function it is necessary to make a call for that stored procedure or function from a program in order to serve the purpose for which it has been created.

Example to create Stored Procedures
```python
import mysql.connector
# creating stored procedure
create_my_proc='''
CREATE PROCEDURE get_emp_detail(ID int)
BEGIN
	SELECT * FROM Employees WHERE name='Aliya';
END;
'''
try:
	# Creating the stored procedure
	mycursor.execute(create_my_proc)
	print("stored procedure created successfully")
except mysql.connector.Error as err:
	print("Error creating stored procedure",err)
# stored procedure created successfully
```

Invoking or Calling the above Stored Procedure
```python
# invoking the stored procedure
try:
	mycursor.callproc("get_emp_detail",args=(1,))
	# faetching the result of stored procedure
	result = mycursor.store_results()
	for row in  result:
		print(row.fetchall())
except mysql.connector.Error as err:
	print("Error invoking stored procedure",err)
# [('Aliya'),('Delhi')]
```
----
Example to create Stored Functions
```python
# sql statement to create the stored function
create_function_query = """
CREATE FUNCTION get_empo(emp_id INT) RETURNS VARCHAR(255)
DETERMINISTIC
BEGIN
	DECLARE emp_name VARCHAR(255);
	SELECT name INTO emp_name FROM emp WHERE id = emp_id;
	RETURN emp_name;
END;
"""

try:
    # creating  the stored function
    mycursor.execute(create_function_query)
    print("Stored function successfully0")
except mysql.connector.Error as err:
    print("Error creating a stored function",err)
# stored function created successfully
```

Invoking or calling the stored function
```python
try:
    # Invoking the stored function within a SELCT Function
    mycursor.execute("SELECT get_emp(1)")
    # Fetching the result of the stored function
    result = mycursor.fetchone()
    print("Employee name : ",result[0] )
except mysql.connector.Error as err:
    print("Error invoking stored function", err)
#
```

Difference between stored procedures and stored functions:
-----

| **STORED PROCEDURES**                                                                                                                                | **STORED FUNCTIONS**                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Stored procedures are precompiled objects which are compiled for the first time and its compiled format is saved, and executes whenever it is called | A function is compiled and executed every time whenever it is called. |
| May or may not returns a value to the calling part of program.                                                                                       | Returns a value to the calling part of the program.                   |
| Uses IN, OUT, IN OUT parameter.                                                                                                                      | Uses only IN parameter.                                               |
| Cannot be called from the function block of code.                                                                                                    | Can be called from the procedure block of code.                       |
| Can call a function from a stored procedure.                                                                                                         | Cannot call a stored procedure from a function.                       |
| Allows the use of Try...Catch blocks to handle exceptions/errors                                                                                     | Does not permit the usage of Try...Catch blocks<br>for error handling |



