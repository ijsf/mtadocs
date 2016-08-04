<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Changes the current default database.

Syntax
------

``` lua
bool mysql_select_db ( MySQLConnection handler, string database )
```

### Required arguments

-   **handler:** A valid MySQL link
-   **database:** The new database name

### Returns

It it succeeds returns true, in other case returns false

Example
-------

**Example 1:** This example changes the current default database to another one

``` lua
local handler = mysql_connect("localhost", "user", "password", "mta_users")
if ( not mysql_select_db(handler, "another_database") ) then
  outputDebugString("Unable to change default database: (" .. mysql_errno(handler) .. ") " .. mysql_error(handler))
end
```

See also
--------
