This function opens a connection to a database and returns an element that can be used with [dbQuery](/dbQuery.md "wikilink"). To disconnect use [destroyElement](/destroyElement.md "wikilink").

Syntax
------

``` lua
element dbConnect ( string databaseType, string host [, string username = "", string password = "", string options = "" ] )
```

### Required Arguments

-   **databaseType:** The type of database. This can be either *sqlite* or *mysql*
-   **host:** The target to connect to. The format of this depends on the database type.
    -   For SQLite it is a [filepath](/filepath.md "wikilink") to a SQLite database file. If the filepath starts with ":/" then the server's global databases directory is used. The file will be created if it does not exist.
    -   For MySQL it is a list of key=value pairs separated by semicolons. Supported keys are:
        -   **dbname**: Name of the database to use e.g. *dbname=test*
        -   **host**: Host address e.g. *host=127.0.0.1*
        -   **port**: Host port e.g. *port=1234* (optional, defaults to standard MySQL port if not used)
        -   **unix\_socket**: Unix socket or named pipe to use (optional)
        -   **charset**: Communicate with the server using a character which is different from the default e.g. *charset=utf8* (optional)

### Optional Arguments

-   **username:** Usually required for MySQL, ignored by SQLite
-   **password:** Usually required for MySQL, ignored by SQLite
-   **options :** List of key=value pairs separated by semicolons. Supported keys are:
    -   **share** which can be set to 0 or 1. (Default value for SQLite is “share=1”, for MySQL is “share=0”). When set to 1, the connection is shared and will be used by other calls to dbConnect with the same host string. This is usually a good thing for SQLite connections, but not so good for MySQL unless care is taken.
    -   **batch** which can be set to 0 or 1. (Default is “batch=1”). When set to 1, queries called in the same frame are automatically batched together which can significantly speed up inserts/updates. The downside is you lose control of the feature that is used to achieve batching (For SQLite it is transactions, for MySQL it is autocommit mode). Therefore, if you use transactions, lock tables or control autocommit yourself, you may want to disable this feature.
    -   **autoreconnect** which can be set to 0 or 1. (Default value “autoreconnect=1”). When set to 1, dropped connections will automatically be reconnected. Note that session variables, user variables, table locks and temporary tables will be reset because of the reconnection. So if you use these fancy features, you will need to turn autoreconnect off and cope with dropped connections some other way.
    -   **log** which can be set to 0 or 1. (Default value “log=1”). When set to 0, activity from this connection will not be recorded in the [database debug log file](/Server_Commands#debugdb.md "wikilink").
    -   **tag** (Default value “tag=script”). A string which helps identify activity from this connection in the [database debug log file](/Server_Commands#debugdb.md "wikilink").
    -   **suppress** A comma separated list of error codes to ignore. (eg. “suppress=1062,1169”).

### Returns

Returns a database connection element unless there are problems, in which case it return *false*.

Example
-------

This example opens a connection to a SQLite database file in the current resource

``` lua
test_db = dbConnect( "sqlite", "file.db" )
```

This example opens a connection to a SQLite database file in another resource

``` lua
test_db = dbConnect( "sqlite", ":resname/file.db" )
```

This example opens a connection to a SQLite database file in the global databases directory

``` lua
test_db = dbConnect( "sqlite", ":/file.db" )
```

This example opens a connection to a SQLite database file in a sub directory of the global databases directory

``` lua
test_db = dbConnect( "sqlite", ":/example/sub/dir/file.db" )
```

This example opens a connection to a MySQL database called 'frank' at server ip 1.2.3.4 and allows the connection to be shared. Note that changing the database or other connection dependent settings affect all connections that are shared.

``` lua
test_db = dbConnect( "mysql", "dbname=frank;host=1.2.3.4", "username", "password", "share=1" )
```

This example opens a connection to a SQLite database is disallows sharing of the connection

``` lua
test_db = dbConnect( "sqlite", "file.db", "", "", "share=0" )
```

This example output debug message, if the connection with SQLite database was established or not

``` lua
test_db = dbConnect( "sqlite", "file.db" )

if test_db then
    outputDebugString( "Connection with database was successfully established." )
else
    outputDebugString( "Connection with database couldn't be established." )
end
```

Requirements
------------

Changelog
---------

See Also
--------

[ru:dbConnect](/ru:dbConnect.md "wikilink")
