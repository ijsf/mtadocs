This function can be used to force the ped to do the choking (coughing) animation until he respawns or toggled off using this function. The animation can not be cancelled by a player it's applied to, and he will not loose health.

Syntax
------

``` lua
bool setPedChoking ( ped thePed, bool choking )
```

### Required Arguments

-   **thePed:** The ped whose choking status to toggle
-   **choking:** *true* to make the ped choke, *false* to no longer force his choking animation

### Returns

Returns *true* if successful, *false* otherwise (e.g. player handle is invalid)

Example
-------

This script will make all players choke on resource start

``` lua
-- Choke all the players when the resource starts
function ResourceStart ()
    setPedChoking ( root, true )
end
addEventHandler ( "onResourceStart", getResourceRootElement (), ResourceStart, true )

-- Unchoke all the players when the resource stops
function ResourceStop ()
    setPedChoking ( root, false )
end
addEventHandler ( "onResourceStop", getResourceRootElement (), ResourceStop, true )

-- Choke players spawning
function PlayerSpawn ()
    setPedChoking ( source, true )
end
addEventHandler ( "onPlayerSpawn", root, PlayerSpawn )
```

See Also
--------

[ru:setPedChoking](/docs/ru:setPedChoking.md "wikilink")
