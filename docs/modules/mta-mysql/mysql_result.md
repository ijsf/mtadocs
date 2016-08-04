<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns a string with the value of the given field with the given offsets, being these:

-   **row\_offset**: An integer value between **1** and **[mysql\_num\_rows()](/docs/modules/mta-mysql/mysql_num_rows.md "wikilink")**
-   **field\_offset**: An integer value between **1** and **[mysql\_num\_fields()](/docs/modules/mta-mysql/mysql_num_fields.md "wikilink")**

If the offset is invalid it returns nil.

Syntax
------

``` lua
string mysql_result ( MySQLResult result, int row_offset, int field_offset )
```

### Required arguments

-   **result:** A valid MySQL result

### Returns

A string with the data contained in the given offset.

See also
--------
