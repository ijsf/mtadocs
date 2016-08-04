This functions queries the MySQL server through the MySQL connection that has been opened by [mysqlOpen](/Modules/MySQL/MysqlOpen.md "wikilink"). The result of the query is then passed to the script by calling callback\_function. It's syntax and functionality is similar to that of [executeSQLSelect](/executeSQLSelect.md "wikilink").

Syntax
------

``` lua
bool mysqlQuery ( mysql mysqlobj, string callback_function, string query )
```

### Required Arguments

-   **mysqlobj** : A *mysql* object created by [mysqlCreate](/Modules/MySQL/MysqlCreate.md "wikilink")
-   **callback\_function** : The function that is called if the operation is done (see below)
-   **query** : The MySQL query that is sent

### Callback Arguments

Your callback function has to accept the following arguments.

On success:

-   **table:** The 2-dimensional table where the results are stored in: table \[row\_index\] \[column\_index\].

On failure:

-   **boolean:** False, when no rows are found or an error occured.

### Optional Arguments

*None*

Example
-------

``` lua
function onMySQLResult ( table )
    outputServerLog ( "Printing some test results" )
    outputServerLog ( table[1][1] )
    outputServerLog ( table[1][2] )
end

function onMySQLOpen ( result )
    if ( result ) then
        outputServerLog ( "MySQL connection established." )
        mysqlQuery ( db, "onMySQLResult", "SELECT * FROM test" )
    else
        outputServerLog ( "MySQL connection failed." )
    end
end

function mysqltest ()
    db = mysqlCreate ()
    mysqlOpen ( db, "onMySQLOpen", "localhost", "bastage", "bastage_pw", "test", 3306 )
end
```
