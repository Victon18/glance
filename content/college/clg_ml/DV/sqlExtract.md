```python
import pandas as pd
import pyodbc
connection = pyodbc.connect("connection string")
sql_query = pd.read_sql_query('Select (ORDER_ID) from ORD',connection)
print (sql_query)

```
---
```python
import pandas as pd
import pyodbc
connection = pyodbc.connect("DRIVER=ODBC Driver 17 for SQL Server;"
                         "SERVER=DESKTOP-QD03NK4\\MSSQLSERVER2022;"  # Use double backslashes for the server name
                        "DATABASE=db1;"  # Replace with your database name
                        "Trusted_connection=yes;"
                         );
sql_query= pd.read_sql_query('select * from tableee',connection)
sql_query.to_csv('tabll.csv')
```

# imports
Import export wizard

connection string
---
Driver name
Server name
database name
trusted connection

```python
conn_str{
    #connection string
}
try:
    conn = pyodbc.connect(conn_str)
    print ("Done")
    cursor= conn.cursor()
    insert_query = """

        """
    data =('pawan','12','mathura','10-01-1900')
    cursor.execute(insert_query,data)
except pyodbc.Error as e:
    print("ERROR",e)
finally:
    if cursor:
        coursor.close()
    if conn:
        conn.close()

```
