<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Executes an unbuffered query in the server and retreives the result.

**`IMPORTANT:`**` It is `**`strongly`**` recommended to call `[`mysql_free_result`](/docs/modules/mta-mysql/mysql_free_result.md "wikilink")` after a query,`
`specially if it returns some data. Query results can be automatically deleted`
`by the lua garbage collector, so if you `**`forget`**` to free a result it will be`
`freed at some time in the future, but it doesn't know the real result data size`
`in memory so it can delay the memory destroying more than it should.`

**`IMPORTANT:`**` Unbuffered queries are to iterate a set of results improving the`
`performance since they are not pre-loaded in memory, so if you execute an unbuffered`
`query you `**`must`**` iterate all the result rows. For more information about unbuffered`
`queries visit `[`http://dev.mysql.com/doc/refman/5.0/en/mysql-use-result.html`](http://dev.mysql.com/doc/refman/5.0/en/mysql-use-result.html)

Syntax
------

``` lua
MySQLResult mysql_unbuffered_query ( MySQLConnection handler, string query )
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
local result = mysql_unbuffered_query(handler, "SELECT * FROM some_table")
if (not result) then
  outputDebugString("Error executing the query: (" .. mysql_errno(handler) .. ") " .. mysql_error(handler))
else
  local numrows = 0
  for result,row in mysql_rows(result) do -- We MUST iterate all the query resulting rows
    numrows = numrows + 1
  end
  outputDebugString("The query returned a total of " .. numrows .. " rows")
  mysql_free_result(result) -- Freeing the result is IMPORTANT
end
```

See also
--------

### Result managing functions

### MySQL handler functions
