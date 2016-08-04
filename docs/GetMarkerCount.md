Returns the number of markers that currently exist in the world.

Syntax
------

``` lua
int getMarkerCount ( )
```

### Required Arguments

*None*

### Returns

Returns the number of markers that currently exist.

Example
-------

This example outputs the amount of markers to the player.

``` lua
function howManyMarkers(thePlayer,command)
    local ammount = getMarkerCount()
    outputChatBox("There are "..ammount.." markers.",thePlayer,255,255,0)
end
addCommandHandler("markers",howManyMarkers)
```

See Also
--------
