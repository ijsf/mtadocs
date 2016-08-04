<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Creates an iterator for the result rows. When this function is called, the row cursor is set to the first result row.

Syntax
------

``` lua
iterator mysql_rows ( MySQLResult result )
```

### Required arguments

-   **result:** A valid MySQL result

### Returns

An iterator function to iterate all the result rows.

### Example

**Example 1:** This example prints all the accounts names

``` lua
local result = mysql_query(handler, "SELECT name FROM account") -- Execute the query
if (result) then
  for result,row in mysql_rows(result) do
    outputDebugString(row[1])
  end
  mysql_free_result(result) -- Free the result
end
```

See also
--------
