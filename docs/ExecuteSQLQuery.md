This function executes an arbitrary SQL query and returns the result rows if there are any. It allows parameter binding for security (SQL injection is rendered impossible).

**NOTE: This function only acts upon registry.db. Use dbQuery to query a custom SQL databse.**

Syntax
------

``` lua
table executeSQLQuery(string query [, var param1 [, var param2 ...]])
```

### Required Arguments

-   **query:** An SQL query. Positions where parameter values will be inserted are marked with a "?".

### Optional Arguments

-   **paramX:** A variable number of parameters. These must be strings or numbers - it is important to make sure they are of the correct type. Also, the number of parameters passed must be equal to the number of "?" characters in the query string.

String parameters are automatically escaped by adding a backslash (\\) before ' and \\ characters.

### Returns

Returns a table with the result of the query if it was a SELECT query, or *false* if otherwise. In case of a SELECT query the result table may be empty (if there are no result rows). The table is of the form:

``` lua
{
    { colname1=value1, colname2=value2, ... },
    { colname1=value3, colname2=value4, ... },
    ...
}
```

Example
-------

Below are examples of equivalents for the deprecated executeSQL functions. Note that \` (backtick) can optionally be used to surround table and row names. It usually a good idea to do this to avoid name clashes with SQL reserved words.

Example equivalents for executeSQLCreateTable:

``` lua
executeSQLQuery("CREATE TABLE IF NOT EXISTS players (clothes_head_texture TEXT, clothes_head_model TEXT, name TEXT)")
executeSQLQuery("CREATE TABLE IF NOT EXISTS `players` (`clothes_head_texture` TEXT, `clothes_head_model` TEXT, `name` TEXT)")
```

Example equivalents for executeSQLDelete:

``` lua
executeSQLQuery("DELETE FROM players WHERE name=?", playerName)
executeSQLQuery("DELETE FROM `players` WHERE `name`=?", playerName)
```

Example equivalents for executeSQLDropTable:

``` lua
executeSQLQuery("DROP TABLE players" )
executeSQLQuery("DROP TABLE `players`" )
```

Example equivalents for executeSQLSelect:

``` lua
executeSQLQuery("SELECT score,health FROM players WHERE name=?", playerName )
executeSQLQuery("SELECT `score`,`health` FROM `players` WHERE `name`=?", playerName )
```

Example equivalents for executeSQLInsert:

``` lua
executeSQLQuery("INSERT INTO players(name,color,sound) VALUES(?,?,?)", playerName, colorName, soundName )
executeSQLQuery("INSERT INTO `players`(`name`,`color`,`sound`) VALUES(?,?,?)", playerName, colorName, soundName )
```

Example equivalents for executeSQLUpdate:

``` lua
executeSQLQuery("UPDATE players SET color='green',sound='somehead' WHERE name=?", playerName )
executeSQLQuery("UPDATE players SET color=?,sound=? WHERE name=?", colorName, soundName, playerName )
executeSQLQuery("UPDATE `players` SET `color`=?,`sound`=? WHERE `name`=?", colorName, soundName, playerName )
```

This example defines a console command that shows the ID's and names of all registered (stored in database) players that have more than the specified amount of money.

``` lua
function listPlayersWithMoreMoneyThan(thePlayer, command, amount)
    local players = executeSQLQuery("SELECT id, name FROM players WHERE money > ?", tonumber(amount))
    outputConsole("Players with more money than " .. amount .. ":", thePlayer)
    for i, playerdata in ipairs(players) do
        outputConsole(playerdata.id .. ": " .. playerdata.name, thePlayer)
    end
end

addCommandHandler("richplayers", listPlayersWithMoreMoneyThan)
```

This example shows the amount of money a certain registered player has.

``` lua
function showPlayerMoney(thePlayer, command, playerName)
    local result = executeSQLQuery("SELECT money FROM players WHERE name=?", playerName)
    if(#result == 0) then
        outputConsole("No player named " .. playerName .. " is registered.", thePlayer)
    else
        outputConsole("Money amount of player " .. playerName .. " is " .. result[1].money, thePlayer)
    end
end
addCommandHandler("playermoney", showPlayerMoney)
```

Notice the lack of single quotes around the "?" in this example, even though it represents a string. executeSQLQuery will see that the playerName variable is a string and take care of the correct execution of the query by itself.

The advantage of using executeSQLQuery is that it is immune to users trying to exploit the query with an SQL injection attack. playerName may contain special characters like ', " or -- that will not influence the query, unlike the older approach where playerName would be concatenated into the query string.

See Also
--------
