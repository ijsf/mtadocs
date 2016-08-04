<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Sets the field cursor of a result in the given field offset. The offset must be a value between **1** and **[mysql\_num\_fields()](/Modules/MTA-MySQL/mysql_num_fields.md "wikilink")**.

Syntax
------

``` lua
int mysql_field_seek ( MySQLResult result, int offset )
```

### Required arguments

-   **result:** A valid MySQL result
-   **offset:** A valid field offset

### Returns

The previous field cursor.

See also
--------
