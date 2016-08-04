<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Converts a string to an hexadecimal representation of it. It is useful to insert binary data in blob fields, or to retreive and show it in your resources. It doesn't append '0x' or 'X' to the retreived string, the programmer must add it.

Syntax
------

``` lua
string mysql_hex_string ( string theString )
```

### Required arguments

-   **theString:** The string to convert

### Returns

An hexadecimal formatted string.

Example
-------

**Example 1:** This function receives a string with a binary file content and stores it in a blob field of the database.

``` lua
function savePlayerAvatar(playerName, imgRawData)
  local imgHexData = mysql_hex_string(imgRawData)
  mysql_query(handler, "UPDATE account SET avatar='0x" .. imgHexData .. "' WHERE name='" .. playerName .. "'")
end
```

See also
--------
