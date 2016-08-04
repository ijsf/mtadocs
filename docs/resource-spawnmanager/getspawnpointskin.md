This function returns the ID of the current skin from a particular spawnpoint.

Syntax
------

``` lua
int getSpawnpointSkin ( spawnpoint spawn )              
```

### Required Arguments

-   **spawn:** A valid spawnpoint element.

### Returns

Returns an [int](/docs/int.md "wikilink") containing the [skin ID](/docs/character_skins.md "wikilink") if the spawnpoint exists, *false* otherwise.

Example
-------

This example outputs the skin, if any, associated with a spawnpoint when a player spawns.

``` lua
function checkPlayerSpawn ( theSpawnpoint )
    local outString = "Player spawned"
    local spawnSkin
        
    if ( theSpawnpoint ) then
        outString = outString .. " on a spawnpoint"
        
        spawnSkin = call(getResourceFromName("spawnmanager"), "getSpawnpointSkin", theSpawnpoint )
        if ( spawnSkin ) then
            outString = outString .. " with skin: " .. tostring(spawnSkin)
        end
    end
    
    outString = outString .. "."
    outputChatBox ( outString )
end
addEventHandler ( "onPlayerSpawn", getRootElement(), checkPlayerSpawn )
```
