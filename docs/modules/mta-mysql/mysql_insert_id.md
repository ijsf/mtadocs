<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass>

Returns the value generated for an AUTO\_INCREMENT field in the last query.

For more information about when is this value updated visit <http://dev.mysql.com/doc/refman/5.0/en/mysql-insert-id.html>

Syntax
------

``` lua
int mysql_insert_id ( MySQLConnection handler )
```

### Required arguments

-   **handler:** A valid MySQL link

### Returns

The value generated for an AUTO\_INCREMENT field in the last query.

Example
-------

**Example 1:** This example creates an account for a player when they use /register, and tells them their database id.

``` lua
function RegisterPlayer(playerSource, commandName, _password)
  local name = mysql_escape_string(handler, getPlayerName(playerSource)) -- Escape the strings to avoid SQL-Injection
  local password = mysql_escape_string(handler, _password)
  local query = "INSERT INTO account SET name='" .. name .. "', password=MD5('" .. password .. "')"

  if (mysql_query(handler, query)) then
    outputChatBox("Account created successfuly with id #" .. mysql_insert_id(handler), playerSource)
  else
    outputChatBox("An error has occured when trying to create your account.", playerSource)
  end
end

addCommandHandler("register", RegisterPlayer)
```

See also
--------
