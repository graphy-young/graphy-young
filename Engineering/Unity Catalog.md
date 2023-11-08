[[Metastore]] [[SaaS]] Provided by [[Databricks]]

## Using Databricks outside of Workspace (Python)
##### Requirements
1. 3.7 <= [[Python]] <= 3.11
2. An existing cluster or [[SQL Warehouse]] to attach ([[SQL Warehouse]] is more recommendable due to lower cost)
3. `databricks-sql-connector` package installed (using `pip install databricks-sql-connector`)
##### Codes
```
import os
from databricks import sql

with sql.connect(server_hostname = os.getenv("DATABRICKS_SERVER_HOSTNAME"),
                 http_path       = os.getenv("DATABRICKS_HTTP_PATH"),
                 access_token    = os.getenv("DATABRICKS_TOKEN")) as connection:
  
    with connection.cursor() as cursor:
      
        # Query data
        cursor.execute("SELECT * FROM catalog.schema.table") # SQL Statements
        result = cursor.fetchall() # Working same as other JDBC/ODBC style code
        for row in result: print(row)
        
        # Create table
        cursor.execute("CREATE TABLE IF NOT EXISTS my_table (col_1 int, col2 int)")

      	# Insert data
        cursor.execute(f"INSERT INTO my_table VALUES (0, 0),(1, 1)")

        # Query metadata
        cursor.columns(schema_name="default", table_name="my_table")
	    print(cursor.fetchall())
        
# Unless you not use context manager, close cursor and connection object manually
# cursor.close()
# connection.close()
```
##### Use [[Python]]-standard `logging` module for debugging

```
import logging # OPTIONAL, If you prefer to configure logging (Databricks uses Python's standard logging)

logging.getLogger("databricks.sql").setLevel(logging.DEBUG)
logging.basicConfig(filename = "results.log", level = logging.DEBUG)

logging.debug(row) # Something to print out like row
```



  
    with connection.cursor() as cursor:
      
        # Query data
        cursor.execute("SELECT * FROM catalog.schema.table") # SQL Statements
        result = cursor.fetchall() # Working same as other JDBC/ODBC style code
        for row in result: logging.debug(row) # OPTIONAL, you can use logging method if you have configured logging 
        
        # Create table
        cursor.execute("CREATE TABLE IF NOT EXISTS squares (x int, x_squared int)")

      	# Insert data
        cursor.execute(f"INSERT INTO squares VALUES (0, 0),(1, 1)")

        # Query metadata
        cursor.columns(schema_name="default", table_name="squares")
	    print(cursor.fetchall())
        
# Unless you not use context manager, close cursor and connection object manually
# cursor.close()
# connection.close()


##### Reference
- https://docs.databricks.com/en/dev-tools/python-sql-connector.html