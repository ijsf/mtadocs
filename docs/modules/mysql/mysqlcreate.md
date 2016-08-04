This function creates a MySQL object which you can use to communicate with a database.

Syntax
------

``` lua
mysql mysqlCreate ( )
```

### Required Arguments

*None*

### Optional Arguments

*None*

Example
-------

``` lua
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
