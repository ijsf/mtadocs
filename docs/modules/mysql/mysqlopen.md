This function opens a MySQL connection to a specific database on a database server. As soon as a connection is made (or timed out), the callback\_function you passed as parameter is called and you can read/write to the database by using the [mysqlQuery](/docs/mysqlQuery.md "wikilink") function.

Syntax
------

``` lua
bool mysqlOpen ( mysql mysqlobj, string callback_function, string host, string user, string password, string database_name, int port )
```

### Required Arguments

-   **mysqlobj** : mysql object (requires an established connection)
-   **callback\_function** : The function that is called if the operation is done (see below)
-   **host** : The database server hostname or IP address to use
-   **user** : The database username to use
-   **password** : The database password to use
-   **database\_name** : The database name to use
-   **port** : The database server port (MySQL default port is *3306*)

### Callback Arguments

Your callback function has to accept the following arguments:

-   **bool** result : Returns false on error, true on success

### Optional Arguments

*None*

Example
-------

``` lua
function onMySQLOpen ( result )
    if ( result ) then
        outputServerLog ( "MySQL connection established." )
    else
        outputServerLog ( "MySQL connection failed." )
    end
end

function mysqltest ()
    db = mysqlCreate ()
    mysqlOpen ( db, "onMySQLOpen", "localhost", "bastage", "bastage_pw", "test", 3306 )
end
```
