<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns a MySQL null type. MySQL NULL and lua nil are different concepts, and a table row can contain NULL values. In this case, you must check the value comparing it to mysql\_null.

Syntax
------

``` lua
MySQLNullValue mysql_null ( )
```

### Returns

A MySQL NULL type.

### Example

**Example 1:** This example checks if the name of an account is null.

``` lua
local result = mysql_query(handler, "SELECT name FROM account WHERE id='1' LIMIT 1") -- Execute the query
if (mysql_result(result, 1, 1) == mysql_null()) then
  outputDebugString("The name of the account #1 is null")
end
mysql_free_result(result) -- Free the result
```

See also
--------
