<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns an associative table containing the current row of the last executed query. You can call this function repeatedly to retreive all the result rows. When there aren't more rows in the result it returns nil. You can go to a specific row calling [mysql\_data\_seek()](/docs/modules/mta-mysql/mysql_data_seek.md "wikilink")

Syntax
------

``` lua
table mysql_fetch_assoc ( MySQLResult result )
```

### Required arguments

-   **result:** A valid MySQL result

### Returns

An associative table with the current row

### Example

**Example 1:** This example shows the name of all the registered accounts

``` lua
local result = mysql_query(handler, "SELECT * FROM account") -- Execute the query
if (result) then
  while true do
    local row = mysql_fetch_assoc(result)
    if (not row) then break end

    outputDebugString(row["name"])
  end
  mysql_free_result(result) -- Free the result
end
```

See also
--------
