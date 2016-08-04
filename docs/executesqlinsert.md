This function adds a row in the database.

The SQLite database contains globally stored data and can be used by scripts to store and retrieve data in a structured manner.

The executed SQL query is the following:

``` sql
INSERT INTO <table> <columns> VALUES <values>
```

Syntax
------

``` lua
bool executeSQLInsert ( string tableName, string values, ( [string columns] ) )
```

### Required Arguments

-   **tableName:** The name of the table you want to modify.
-   **values:** The values that need to be inserted for each field in the table. The ' character is used to specify a value and , is used as a delimiter for multiple values (e.g. '' 'value1','value2','value3' ''. The value order corresponds to either the default column order in the table, or the optional column argument (see below).

### Optional Arguments

-   **columns:** The columns where the values will be stored into. This corresponds with the given value order (your first column will be set to the first specified value, the second column to the second value, ...) and should be separated by the , delimiter.

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
    local sourcename = getPlayerName ( source )         -- get the player's name
    
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
    outputChatBox ( "Your head texture is " .. result[1].clothes_head_texture )
    outputChatBox ( "Your head model is " .. result[1]['clothes_head_model'] )  
end
addEventHandler ( "onPlayerSpawn", getRootElement(), addInfoToSQL)
```

See Also
--------
