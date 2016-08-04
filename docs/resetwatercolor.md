This function reset the water color of the GTA world to default.

Syntax
------

``` lua
bool resetWaterColor ( )
```

### Returns

Returns *true* if water color was reset correctly, *false* otherwise.

Example
-------

This example adds a command *resetwatercolor* with which a player can reset the water colour.

``` lua
function changeWaterBackToNormal ()
    resetWaterColor ()
end
addCommandHandler ( "resetwatercolor", changeWaterBackToNormal )
```

See Also
--------
