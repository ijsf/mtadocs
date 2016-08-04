This function resets the water of the GTA world back to its default level. [Water elements](/water.md "wikilink") are not affected.

Syntax
------

``` lua
bool resetWaterLevel ()
```

### Returns

Returns *true* if water level was reset correctly, *false* otherwise.

Example
-------

This example adds a command *resetwaterlevel* with which a player can reset the water level.

``` lua
function changeWaterLevelBackToNormal ()
    resetWaterLevel ()
end
addCommandHandler ( "resetwaterlevel", changeWaterLevelBackToNormal )
```

Requirements
------------

See Also
--------
