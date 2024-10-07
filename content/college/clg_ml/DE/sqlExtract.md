```python
import pandas as pd
import pyodbc
connection = pyodbc.connect("connection string")
sql_query = pd.read_sql_query('Select (ORDER_ID) from ORD',connection)
print (sql_query)

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
    conn = pydoc.connect(conn_str)
    print ("Done")
    cursor= conn.cursor()
    insert_query = """

        """
    data =('pawan','12','mathura','10-01-1900')
    cursor.execute()
except pydoc.Error as e:
    print("ERROR",e)
finally:

```
