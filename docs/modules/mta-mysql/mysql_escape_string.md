<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Escapes a query string to avoid sql injection attacks. This function should be used for every executed query that uses any data given by the players.

Syntax
------

``` lua
string mysql_escape_string( MySQLConnection handler, string theString )
```

### Required arguments

-   **handler:** A valid MySQL link
-   **theString:** The string to escape

### Returns

The escaped string

Example
-------

**Example 1:** This example returns some offline player cash getting it from the database

``` lua
function checkOfflineMoney(playerSource, commandName, targetName)
  local escapedName = mysql_escape_string(handler, targetName) -- Escape the string to avoid security holes
  local result = mysql_query(handler, "SELECT money FROM account WHERE name='" .. escapedName .. "'")
  if (not result) then
    outputDebugString("mysql_query failed: (" .. mysql_errno(handler) .. ") " .. mysql_error(handler)) -- Some error occurred
  else
    if (mysql_num_rows(result) == 0) then outputChatBox("Account not found", playerSource) -- We haven't results with that name
    else outputChatBox("The player has " .. mysql_result(result, 1, 1) .. "$", playerSource) end -- Send the money information
    mysql_free_result(result) -- Free the query result
  end
end
addCommandHandler("offlinecash", checkOfflineMoney)
```

See also
--------
