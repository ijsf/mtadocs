This function returns the current rotation of the specified spawnpoint.

Syntax
------

``` lua
float getSpawnpointRotation ( spawnpoint theSpawn )             
```

### Required Arguments

-   **theSpawn:** The spawnpoint element to get rotation of.

### Returns

Returns the rotation as a [float](/docs/float.md "wikilink") if the spawnpoint is valid, *false* otherwise.

Example
-------

This example outputs the rotation associated with a spawnpoint when a player spawns.

``` lua
function checkPlayerSpawn ( theSpawnpoint )
    local outString = "Player spawned"
    local spawnRotation
        
    if ( theSpawnpoint ) then
        outString = outString .. " on a spawnpoint"
        
        spawnRotation = call(getResourceFromName("spawnmanager"), "getSpawnpointRotation", theSpawnpoint )
        if ( spawnRotation ) then
            outString = outString .. " with rotation: " .. tostring(spawnRotation)
        end
    end
    
    outString = outString .. "."
    outputChatBox ( outString )
end
addEventHandler ( "onPlayerSpawn", getRootElement(), checkPlayerSpawn )
```
