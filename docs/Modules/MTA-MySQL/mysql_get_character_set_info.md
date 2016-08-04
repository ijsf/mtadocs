<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Retreives information about a character set

Syntax
------

``` lua
string, string, string, string, int, int mysql_get_character_set_info ( MySQLConnection handler, string character_set_name )
```

### Required arguments

-   **handler:** A valid MySQL link
-   **character\_set\_name:** The character set name

### Returns

The character set information:

-   The charset name
-   The charset collation
-   The charset comment
-   The charset directory
-   Multi byte character min. length
-   Multi byte character max. length

Example
-------

**Example 1:**

``` lua
local name, collation, comment, directory, mbminlen, mbmaxlen =
      mysql_get_character_set_info(handler, "utf8") -- We will return information about the charset "utf8"

outputDebugString("UTF-8 charset information:\n" ..
                  "name: " .. name .. "\n" ..
                  "collation: " .. collation .. "\n" ..
                  "comment: " .. comment .. "\n" ..
                  "directory: " .. directory .. "\n" ..
                  "mbminlen: " .. mbminlen .. "\n" ..
                  "mbmaxlen: " .. mbmaxlen)
```

See also
--------
