<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Creates an iterator for the result fields. When this function is called, the field cursor is set to the first field.

Syntax
------

``` lua
iterator mysql_fields ( MySQLResult result )
```

### Required arguments

-   **result:** A valid MySQL result

### Returns

An iterator function to iterate all the result fields.

### Example

**Example 1:** This example shows how to print the rows of a result set showing the field name.

``` lua
local result = mysql_query(handler, "SELECT * FROM account") -- Execute the query
for result,row in mysql_rows(result) do -- Iterate through all the result rows
  local i = 1
  for result,field in mysql_fields(result) do
    if (row[i] ~= mysql_null()) then
      outputDebugString("row[" .. field["name"] .. "] = " .. row[i])
    else
      outputDebugString("row[" .. field["name"] .. "] = NULL")
    end
    i = i + 1
  end
end
mysql_free_result(result) -- Free the result
```

See also
--------
