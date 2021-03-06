This function creates a spawnpoint.

Syntax
------

``` lua
spawnpoint createSpawnpoint ( float x, float y, float z, [ float rotation = 0, int skin = 0,  int interior = 0, int dimension = 0 ] )
```

### Required Arguments

-   **x**: A floating point number representing the X coordinate on the map.
-   **y**: A floating point number representing the Y coordinate on the map.
-   **z**: A floating point number representing the Z coordinate on the map.
-   **rotation:** A floating point number representing the spawn's rotation about the Z axis in degrees.
-   **skin:** An integer representing the skin ID (see [character skins](/docs/character_skins.md "wikilink")).
-   **interior:** An integer representing the interior in which the spawnpoint spawns players.
-   **dimension:** An integer representing the diimension in which the spawnpoint spawns players.

### Returns

Returns the spawnpoint element if creation was successful, *false* otherwise.

Example
-------

This function lets the player create a new spawnpoint where he stands, with the skin of his choice.

``` lua
local spawnpointsTable = { }
 
function createSpawnpointCmd(player,cmd,arg1)
    local x, y, z = getElementPosition(player)
    local rot = getPlayerRotation(player)
    local int = getElementInterior(player)
    local dim = getElementDimension(player)
    local skin = getElementModel(player)
   
    local spawnpoint = exports.spawnmanager:createSpawnpoint(x, y, z, rot, skin, int, dim)
   
    if spawnpoint then
        table.insert(spawnpointsTable, spawnpoint)
         outputChatBox("Created Spawn Point", player)
    else
         outputChatBox("Failed to create Spawn Point", player)
    end
end
addCommandHandler("mark",createSpawnpointCmd)
```
