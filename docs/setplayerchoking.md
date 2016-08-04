This function can be used to force the player to do the choking animation (teargas etc...) until he respawns or toggled off using this function. The animation can not be cancelled by the player and he will not loose health.

Syntax
------

``` lua
bool setPlayerChoking ( player thePlayer, bool choking )
```

### Required Arguments

-   **thePlayer:** Define the player whose choking status to toggle
-   **choking:** Use true to make the player choke, false to no longer force his choking animation

### Returns

Returns *true* if successful, *false* otherwise (e.g. player handle is invalid)

Example
-------

This script will make all players choke on resource start

``` lua
-- Choke all the players when the resource starts
function ResourceStart ()
    setPlayerChoking ( root, true )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource () ), ResourceStart, true )

-- Unchoke all the players when the resource stops
function ResourceStop ()
    setPlayerChoking ( root, false )
end
addEventHandler ( "onResourceStop", getResourceRootElement ( getThisResource () ), ResourceStop, true )

-- Choke players spawning
function PlayerSpawn ()
    setPlayerChoking ( source, true )
end
addEventHandler ( "onPlayerSpawn", root, PlayerJoin )
```

See Also
--------
