<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Checks if the given MySQL connection is still alive.

Syntax
------

``` lua
bool mysql_ping ( MySQLConnection handler )
```

### Required arguments

-   **handler:** A valid MySQL link

### Returns

true is the connection is still alive, false if not.

Example
-------

**Example 1:** This example checks if the MySQL connection is still alive when a player connects, to be able to fetch their data.

``` lua
myhandler = mysql_connect("localhost", "user", "password", "mta_users")

function checkMySQLConnection ( )
  if (mysql_ping(myhandler) == false) then -- We lost the connection to the MySQL server
    outputDebugString("Lost connection to the MySQL server, reconnecting ...")
    mysql_close(myhandler)
    myhandler = mysql_connect("localhost", "user", "password", "mta_users") -- Reconnect to the MySQL server
  end
end

addEventHandler("onPlayerJoin", getRootElement(), checkMySQLConnection)
```

See also
--------
