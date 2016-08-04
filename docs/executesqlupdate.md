This function updates one or more rows in the database, by using the set parameter and conditions to change field values in specific rows.

The SQLite database contains globally stored data and can be used by scripts to store and retrieve data in a structured manner.

The executed SQL query is the following:

``` sql
UPDATE <table> SET <set> WHERE <conditions>
```

Syntax
------

``` lua
bool executeSQLUpdate ( string tableName, string set, [ string conditions ] )
```

### Required Arguments

-   **tableName:** The name of the table you want to modify.
-   **set:** The query you want to execute on that table. The default SQL syntax is used, which means that the = is used to set a value and the ' is used to specify a value (e.g. ''test = 'hi' ''). The , is used as a delimiter for multiple queries.

### Optional Arguments

-   **conditions:** The conditions that need to be met before a specific row is changed.

### Returns

The function returns *true* on success, and *false* on failure.

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
    if ( result == false ) then -- see if any data was found at all
        outputChatBox ( "This is your first time here! Welcome " .. sourcename .. "!", source )
        executeSQLInsert ( "players", "'none', 'none', '" .. sourcename .. "'" )
    else
        outputChatBox ( "Welcome back " .. sourcename .. "!", source )
        executeSQLUpdate ( "players", "clothes_head_texture = 'hairgreen', clothes_head_model = 'somehead'",
        "player = '" .. sourcename .. "'" )
    end 
    
    -- get the clothes data for the player
    result = executeSQLSelect ( "players", "clothes_head_texture, clothes_head_model", "player = '" .. sourcename .. "'" )
    outputChatBox ( "Your head texture is " .. result[1][1] )
    outputChatBox ( "Your head model is " .. result[1][2] ) 
end
addEventHandler ( "onPlayerSpawn", getRootElement(), addInfoToSQL )
```

See Also
--------
