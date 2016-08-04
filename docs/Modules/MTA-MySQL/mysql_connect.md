<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Makes a connection to a MySQL server and returns a handler to it.

Syntax
------

``` lua
MySQLConnection mysql_connect ( string hostname, string username, string password, string database, [ int port=3306, string unix_socket=nil, string client_flags=""] )
```

### Required arguments

-   **hostname:** The hostname to connect to
-   **username:** The database username
-   **password:** The username password
-   **database:** The starting database

### Optional arguments

-   **port**: The MySQL port
-   **unix\_socket**: When connecting in unix systems to a local database, the path for the unix socket (usually /var/run/mysqld/mysqld.sock)
-   **client\_flags**: The connection flags, with the format *“flag1|flag2|flag3”*. The list of flags is:
    -   **compress:** Use compression protocol.
    -   **found\_rows:** Return the number of found (matched) rows, not the number of changed rows.
    -   **ignore\_sigpipe:** Prevents the client library from installing a SIGPIPE signal handler. This can be used to avoid conflicts with a handler that the application has already installed.
    -   **ignore\_space:** Allow spaces after function names. Makes all functions names reserved words.
    -   **interactive:** Allow interactive\_timeout seconds (instead of wait\_timeout seconds) of inactivity before closing the connection. The client's session wait\_timeout variable is set to the value of the session interactive\_timeout variable.
    -   **local\_files:** Enable LOAD DATA LOCAL handling.
    -   **no\_schema:** Don't allow the db\_name.tbl\_name.col\_name syntax. This is for ODBC. It causes the parser to generate an error if you use that syntax, which is useful for trapping bugs in some ODBC programs.

### Returns

A valid MySQL handler if it was able to connect, or nil if it was unable.

Example
-------

**Example 1:** This example makes a MySQL connection and checks if it was succesful.

``` lua
handler = mysql_connect("localhost", "username", "password", "mta_users") -- Establish the connection
if ( not handler ) then -- The connection failed
  outputDebugString("Unable to connect to the MySQL server")
else
  mysql_close(handler) -- Close the connection
end
```

**Example 2:** This example makes a MySQL connection and set charset

``` lua
local charset = "utf8";
local handler = mysql_connect("127.0.0.1", "username", "password", "database", 3306, "/var/lib/libmysqlclient.so.15", "")

if (handler) then
    mysql_query(handler, "SET NAMES '"..charset.."'")
    mysql_query(handler, "SET OPTION CHARACTER SET "..charset.."")
    mysql_query(handler, "SET CHARACTER SET '"..charset.."'")
end
```

See also
--------
