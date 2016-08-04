This function retrieves rows from a table in the database, if they exist. If you pass the table name, along with the columns you want to retrieve (and any conditions for the row) this function will return a table containing the corresponding values.

The SQLite database contains globally stored data and can be used by scripts to store and retrieve data in a structured manner.

The executed SQL query is the following:

``` sql
SELECT <fields> FROM <tables> WHERE <conditions> LIMIT <limit>
```

Syntax
------

``` lua
table executeSQLSelect ( string tableName, string fields, [ string conditions, int limit ] )
```

### Required Arguments

-   **tableName:** The table you want to query. No spaces allowed.
-   **fields:** The fields you want to query. No spaces allowed. Multiple fields should be separated by a comma (,). Wildcard (\*) allowed to query all fields in the table. If you use wildcards, please pay attention to the order in which you'll have to retrieve your values from the table.

### Optional Arguments

-   **conditions:** The conditions for the query. Multiple conditions should be separated by logical operators (AND, OR).
-   **limit:** Maximum amount of rows to return.

### Returns

Returns a 2-dimensional table where the results are stored as table \[row\_index\] \[column\_name\]. Please note that table may be empty.

If invalid arguments were passed, returns *false*.

Example
-------

This example creates a SQL table when a map loads, and stores info about a player to that database when he spawns.

``` lua
function onMapLoad ()
    -- create our table, if it doesn't already exist
    executeSQLCreateTable ( "players", "clothes_head_texture TEXT, clothes_head_model TEXT, player TEXT" )
end
addEventHandler ( "onGamemodeMapStart", getRootElement(), onMapLoad )

function addInfoToSQL( theSpawnpoint, theTeam ) 
    sourcename = getPlayerName ( source )   -- get the player's name
    
    -- try to retrieve the player data from the db
    result = executeSQLSelect ( "players", "player", "player = '" .. sourcename .. "'" )
    if ( type( result ) == "table" and #result == 0 ) or not result then -- see if any data was found at all
        outputChatBox ( "This is your first time here! Welcome " .. sourcename .. "!", source )
        executeSQLInsert ( "players", "'none', 'none', '" .. sourcename .. "'" )
    else
        outputChatBox ( "Welcome back " .. sourcename .. "!", source )
        executeSQLUpdate ( "players", "clothes_head_texture = 'hairgreen', clothes_head_model = 'somehead'",
        "player = '" .. sourcename .. "'" )
    end 
    
    -- get the clothes data for the player
    result = executeSQLSelect ( "players", "clothes_head_texture, clothes_head_model", "player = '" .. sourcename .. "'" )
    outputChatBox ( "Your head texture is " .. result[1].clothes_head_texture )
    outputChatBox ( "Your head model is " .. result[1]['clothes_head_model'] )  
end
addEventHandler ( "onPlayerSpawn", getRootElement(), addInfoToSQL )
```

See Also
--------

[ru:executeSQLSelect](/docs/ru:executesqlselect.md "wikilink")
