<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns the name of a given field in the last executed query. The offset of the field must be an integer between **1** and **[mysql\_num\_fields()](/Modules/MTA-MySQL/mysql_num_rows/mysql_num_fields.md "wikilink")**

Syntax
------

``` lua
int mysql_field_name ( MySQLResult result, int offset )
```

### Required arguments

-   **result:** A valid MySQL result
-   **offset:** A valid offset

### Returns

The given field name.

### Example

**Example 1:**

``` lua
local result = mysql_query(handler, "SELECT name FROM account WHERE id='1' LIMIT 1") -- Execute the query
if (result) then
  local str = mysql_field_name(result, 1)
  outputDebugString(str) -- Will print 'name'
  mysql_free_result(result) -- Free the result
end
```

See also
--------
