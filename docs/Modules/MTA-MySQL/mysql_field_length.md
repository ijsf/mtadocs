<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns the length of a given field in the last retreived row. The offset of the field must be an integer between **1** and **[mysql\_num\_fields()](/docs/Modules/MTA-MySQL/mysql_num_fields.md "wikilink")**

Syntax
------

``` lua
int mysql_field_length ( MySQLResult result, int offset )
```

### Required arguments

-   **result:** A valid MySQL result
-   **offset:** A valid offset

### Returns

The given field data length.

### Example

**Example 1:**

``` lua
local result = mysql_query(handler, "SELECT name FROM account WHERE id='1' LIMIT 1") -- Execute the query
if (result) then
  local row = mysql_fetch_row(result)
  local length = mysql_field_length(result, 1)
  outputDebugString("The length of " .. row[1] .. " is " .. length)
  mysql_free_result(result) -- Free the result
end
```

See also
--------
