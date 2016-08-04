<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Closes an established connection to a MySQL server.

Syntax
------

``` lua
mysql_close ( MySQLConnection handler )
```

### Required arguments

-   **handler:** A valid MySQL link

### Returns

This function doesn't return any value

Example
-------

**Example 1:** This example makes a MySQL connection and then closes it

``` lua
handler = mysql_connect("localhost", "username", "password", "mta_users") -- Establish the connection
if ( not handler ) then -- The connection failed
  outputDebugString("Unable to connect to the MySQL server")
else
  mysql_close(handler) -- Close the connection
end
```

See also
--------
