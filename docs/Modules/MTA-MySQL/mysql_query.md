<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Executes a query in the server and retreives the result.

**`IMPORTANT:`**` It is `**`strongly`**` recommended to call `[`mysql_free_result`](/Modules/MTA-MySQL/mysql_free_result.md "wikilink")` after a query,`
`specially if it returns some data. Query results can be automatically deleted`
`by the lua garbage collector, so if you `**`forget`**` to free a result it will be`
`freed at some time in the future, but it doesn't know the real result data size`
`in memory so it can delay the memory destroying more than it should.`

Syntax
------

``` lua
MySQLResult mysql_query ( MySQLConnection handler, string query )
```

### Required arguments

-   **handler:** A valid MySQL link
-   **query:** The executing query

### Returns

In case of error this function returns nil. IF not, a MySQLResult handler. Check the MySQL result managing functions to see how to retreive the data from it.

Example
-------

**Example 1:**

``` lua
local result = mysql_query(handler, "SELECT * FROM some_table")
if (not result) then
  outputDebugString("Error executing the query: (" .. mysql_errno(handler) .. ") " .. mysql_error(handler))
else
  mysql_free_result(result) -- Freeing the result is IMPORTANT
end
```

See also
--------

### Result managing functions

### MySQL handler functions
