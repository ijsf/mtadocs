<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Sets the row cursor of a result in the given row offset. The offset must be a value between **1** and **[mysql\_num\_rows()](/Modules/MTA-MySQL/mysql_num_rows.md "wikilink")**.

Syntax
------

``` lua
mysql_data_seek ( MySQLResult result, int offset )
```

### Required arguments

-   **result:** A valid MySQL result
-   **offset:** A valid row offset

### Returns

This function doesn't return any value.

See also
--------
