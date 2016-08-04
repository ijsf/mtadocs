This event triggers whenever a pickup is left clientside.

Parameters
----------

``` lua
player thePlayer, bool matchingDimension
```

-   **thePlayer:** the player that left the pickup
-   **matchingDimension:** *true* if thePlayer is in the same dimension as the pickup, *false* otherwise.

Source
------

The source of this event is the pickup that was left.

Example
-------

This example outputs a message whenever a player leaves a pickup locally.

``` lua
local function clientPickupLeave(thePlayer, matchingDimension)
    outputChatBox("* "..getPlayerName(thePlayer).." left a pickup!", 255, 0, 0)
end
addEventHandler("onClientPickupLeave", root, clientPickupLeave)
```

See Also
--------

### Client pickup events

### Client player events

### Client event functions
