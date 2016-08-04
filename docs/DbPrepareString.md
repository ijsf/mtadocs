Syntax
------

``` lua
string dbPrepareString ( element databaseConnection, string query [, var param1 [, var param2 ...]] )
```

### Required Arguments

-   **databaseConnection:** A database connection element previously returned from [dbConnect](/dbConnect.md "wikilink")
-   **query:** An SQL query. Positions where parameter values will be inserted are marked with a **?**

### Optional Arguments

-   **paramX:** A variable number of parameters. These must be strings or numbers - it is important to make sure they are of the correct type. Also, the number of parameters passed must be equal to the number of **?** characters in the query string.

String parameters are automatically quoted and escaped as required. (If you do not want a string quoted, use **??**)

### Returns

Returns a prepare SQL query string, or *false* if an error occurred.

Example
-------

This example shows how to safely build a dynamic SELECT query

``` lua
serialsToUse = { "111", "222", "333" }

local queryString = dbPrepareString( connection, "SELECT * FROM `player_info` WHERE true" )
for _,serial in ipairs(serialsToUse) do
    queryString = queryString .. dbPrepareString( connection, " AND `serial`=?", serial )
end
local handle = dbQuery( connection, queryString )
```

This example shows how to build an INSERT/UPDATE query for multiple rows. (Query syntax is MySQL only and assumes one column is a unique key)

``` lua
local queryString = dbPrepareString( connection, "INSERT INTO `player_info` (name,serial,ispoopoohead) VALUES " )
for idx,info in ipairs(playerInfos) do
    if idx > 1 then
        queryString = queryString . ","
    end
    queryString = queryString . dbPrepareString( connection, "(?,?,?)", info.name, info.serial, info.ispoopoohead )
end
queryString = queryString . dbPrepareString( connection, " ON DUPLICATE KEY UPDATE name=VALUES(name),serial=VALUES(serial),ispoopoohead=VALUES(ispoopoohead) " )
dbExec( connection, queryString );
```

Requirements
------------

See Also
--------
