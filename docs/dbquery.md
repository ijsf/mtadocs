This function starts a database query using the supplied connection. Use the returned query handle with [dbPoll](/docs/dbpoll.md "wikilink") to get the result, or [dbFree](/docs/dbfree.md "wikilink") if you don't want the result.

Syntax
------

``` lua
handle dbQuery ( [ function callbackFunction, [ table callbackArguments, ] ] element databaseConnection, string query [, var param1 [, var param2 ...]] )
```

### Required Arguments

-   **databaseConnection:** A database connection element previously returned from [dbConnect](/docs/dbconnect.md "wikilink")
-   **query:** An SQL query. Positions where parameter values will be inserted are marked with a **?**

### Optional Arguments

-   **callbackFunction:** An optional function to be called when a result is ready. The function will only be called if the result has not already been read with [dbPoll](/docs/dbpoll.md "wikilink"). The function is called with the query handle as the first argument. (Notice: Do not use a function with a local prefix)
-   **callbackArguments:** An optional table containing extra arguments to be sent to the callback function.
-   **paramX:** A variable number of parameters. These must be strings or numbers - it is important to make sure they are of the correct type. Also, the number of parameters passed must be equal to the number of **?** characters in the query string.

String parameters are automatically quoted and escaped as required. (If you do not want a string quoted, use **??**)

### Returns

Returns a query handle unless the connection is incorrect, in which case it return *false*.

Example
-------

This example starts an INSERT query and frees the result:

``` lua
local qh = dbQuery( connection, "INSERT INTO table_name VALUES (?,?,?)", "aaa", "bbb", 10 )
dbFree( qh )
```

This example starts a select query and waits for the result: (server freeze included)

``` lua
local qh = dbQuery( connection, "SELECT * FROM table_name" )
local result = dbPoll( qh, -1 )
```

This example starts a select query and processes the result in a callback function:

``` lua
function aaa()
    dbQuery( myCallback, connection, "SELECT * FROM table_name" )
end

function myCallback(qh)
    local result = dbPoll( qh, 0 )   -- Timeout doesn't matter here because the result will always be ready
end
```

This example starts a select query and processes the result in an inline callback function with custom arguments:

``` lua
dbQuery( function(qh, tag, score)
            local result = dbPoll( qh, 0 )   -- Timeout doesn't matter here because the result will always be ready
            outputDebugString( tag )         -- Prints "hello"
            outputDebugString( score )       -- Prints 2000
         end
         ,{"hello",2000}, connection, "SELECT * FROM table_name" )
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
