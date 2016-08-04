This function escapes a given string so it's safe to pass as a query to [mysqlQuery](/Modules/MySQL/MysqlQuery.md "wikilink"). Please use this as sanity checking function to prevent bad things like SQL injection.

The function needs an already established connection to a MySQL database, because it reads out the character set from that database to escape the string.

Syntax
------

``` lua
string mysqlSafeString ( mysql mysqlobj, string query )
```

### Required Arguments

-   **mysqlobj** : A *mysql* object created by [mysqlCreate](/Modules/MySQL/MysqlCreate.md "wikilink")
-   **query** : The MySQL query that needs to be escasped

### Optional Arguments

*None*

Example
-------

``` lua
function onMySQLOpen ( result )
    if ( result ) then
        outputServerLog ( "MySQL connection established." )
        -- do the safe query
        local safe = mysqlSafeString ( db, some_string_passed_by_a_user )
        mysqlQuery ( db, "onMySQLResult", "SELECT ".. safe .." FROM test" )
    else
        outputServerLog ( "MySQL connection failed." )
    end
end

function mysqltest ()
    db = mysqlCreate ()
    mysqlOpen ( db, "onMySQLOpen", "localhost", "bastage", "bastage_pw", "test", 3306 )
end
```
