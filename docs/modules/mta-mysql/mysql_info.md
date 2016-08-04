<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns a string with information of the last executed query.

For more information about the possible returned values please visit <http://dev.mysql.com/doc/refman/5.0/en/mysql-info.html>

Syntax
------

``` lua
string mysql_info ( MySQLConnection handler )
```

### Required arguments

-   **handler:** A valid MySQL link

### Returns

A string with the last executed query information.

See also
--------
