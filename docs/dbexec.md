This function executes a database query using the supplied connection. No result is returned.

Syntax
------

``` lua
bool dbExec ( element databaseConnection, string query [, var param1 [, var param2 ...]] )
```

### Required Arguments

-   **databaseConnection:** A database connection element previously returned from [dbConnect](/docs/dbConnect.md "wikilink")
-   **query:** An SQL query. Positions where parameter values will be inserted are marked with a **?**

### Optional Arguments

-   **paramX:** A variable number of parameters. These must be strings or numbers - it is important to make sure they are of the correct type. Also, the number of parameters passed must be equal to the number of **?** characters in the query string.

String parameters are automatically quoted and escaped as required. (If you do not want a string quoted, use **??**)

### Returns

Returns *true* unless the connection is incorrect, in which case it returns *false*.

Example
-------

This example executes an INSERT query:

``` lua
dbExec( connection, "INSERT INTO table_name VALUES (?,?,?)", "aaa", "bbb", 10 )
```

This example shows how to use **??** for parts of the query that are not column values:

``` lua
dbExec( connection, "UPDATE ?? SET ??=?", tableName, columnName, columnValue )
```

***Note**: It is usually good practice to surround table and column names with backticks (\`) in case they contain spaces or SQL keywords (and therefore cause syntax errors). This is especially true when using variables for table and column names, as potential problems may not be apparent when the script is first written.*
This example shows how to use backticks and **??** for parts of the query that are not column values:

``` lua
dbExec( connection, "UPDATE `??` SET `??`=?", tableName, columnName, columnValue )
```

Requirements
------------

See Also
--------
