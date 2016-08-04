<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Frees the last query result. This function should be called after every query, specially when these queries return any data.

Syntax
------

``` lua
mysql_free_result ( MySQLResult result )
```

### Required arguments

-   **result:** A valid MySQL result

### Returns

This function doesn't return any value.

See also
--------
