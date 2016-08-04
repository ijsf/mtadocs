This event triggers whenever a pickup is hit clientside.

Parameters
----------

``` lua
player thePlayer, bool matchingDimension
```

-   **thePlayer:** the player that hit the pickup
-   **matchingDimension:** *true* if thePlayer is in the same dimension as the pickup, *false* otherwise.

Source
------

The source of this event is the pickup that was hit.

Example
-------

This example outputs a message whenever a player hits a pickup locally.

``` lua
local function clientPickupHit(thePlayer, matchingDimension)
    outputChatBox("* "..getPlayerName(thePlayer).." hit a pickup!", 255, 0, 0)
end
addEventHandler("onClientPickupHit", root, clientPickupHit)
```

See Also
--------

### Client pickup events

### Client player events

### Client event functions
