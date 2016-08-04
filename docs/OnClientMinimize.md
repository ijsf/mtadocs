This event is triggered when the local player minimizes the game screen.

Parameters
----------

*None*

Example
-------

This example kills any player who minimizes the game.

``` lua
function handleMinimize()
    setElementHealth( localPlayer, 0 )
end
addEventHandler( "onClientMinimize", root, handleMinimize )
```

See Also
--------

### Other client events

### Client event functions
