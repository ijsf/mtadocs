<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns a table containing the length of the values of the last retreived row. If you didn't retreive any row or you are in the end of the result set, it returns nil.

Syntax
------

``` lua
table mysql_fetch_lengths ( MySQLResult result )
```

### Required arguments

-   **result:** A valid MySQL result

### Returns

A table with the length of the values of the last retreived row.

### Example

**Example 1:** This example shows the length of an account name

``` lua
local result = mysql_query(handler, "SELECT name FROM account WHERE id='1' LIMIT 1") -- Execute the query
if (result) then
  local row = mysql_fetch_row(result) -- Return the resulting row
  local lengths = mysql_fetch_lengths(result) -- Retreive the lengths of the result fields
  outputDebugString("The length of " .. row[1] .. " is " .. lengths[1])
  mysql_free_result(result) -- Free the result
end
```

See also
--------
