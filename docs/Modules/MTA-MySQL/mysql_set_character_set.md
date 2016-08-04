<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Changes the character set used for the current MySQL session.

Syntax
------

``` lua
bool mysql_set_character_set ( MySQLConnection handler, string charset_name )
```

### Required arguments

-   **handler:** A valid MySQL link
-   **charset\_name:** The new character set name

### Returns

It it succeeds returns true, in other case returns false.

Example
-------

**Example 1:**

``` lua
handler = mysql_connect("localhost", "user", "password", "mta_users")
if (not handler) then
  outputDebugString("Unable to connect to the MySQL server")
elseif (not mysql_set_character_set(handler, "utf8")) then -- Change the charset to UTF-8
  outputDebugString("Unable to change the connection character set to utf8: ("
                    .. mysql_errno(handler) .. ")" .. mysql_error(handler))
  mysql_close(handler) -- Close the connection afther the error
end
```

See also
--------
