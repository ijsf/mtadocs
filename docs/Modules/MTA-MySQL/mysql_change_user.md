<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Changes the current MySQL session authentication.

Syntax
------

``` lua
bool mysql_change_user ( MySQLConnection handler, string new_username, string new_password [, string new_database ] )
```

### Required arguments

-   **handler:** A valid MySQL link
-   **new\_username:** The new username
-   **new\_password:** The new username password

### Optional arguments

-   **new\_database:** Start the new session using a new default database

### Returns

It it succeeds returns true, in other case returns false

Example
-------

**Example 1:**

``` lua
function resourceStart ( res )
  if (res == getThisResource()) then
    myhandler = mysql_connect("localhost", "writer_user", "password", "mta_users") -- Start with a read-write username
    if (not myhandler) then
      outputDebugString("Unable to connect to the database: (" .. mysql_errno(handler) .. ") " .. mysql_error(handler))
    else
      -- Apply some changes to the database here
      if (not mysql_change_user(myhandler, "localhost", "reader_user", "password", "mta_users")) then -- Change to a read-only user
        outputDebugString("Unable to set the database read-only user: (" ..
                           mysql_errno(handler) .. ") " .. mysql_error(handler))
        mysql_close(myhandler) -- Close the MySQL connection
      end
    end
  end
end

addEventHandler("onResourceStart", getRootElement(), resourceStart)
```

See also
--------
