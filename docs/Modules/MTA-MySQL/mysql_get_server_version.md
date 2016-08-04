<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns a number that represents the MySQL server version in this format:

`major_version*10000 + minor_version *100 + sub_version`

For example, 5.0.12 is returned as 50012.

This function is useful in client programs for quickly determining whether some version-specific server capability exists.

Syntax
------

``` lua
int mysql_get_server_version( MySQLConnection handler )
```

### Required arguments

-   **handler:** A valid MySQL link

### Returns

An integer representing the MySQL server version.

See also
--------
