Sets the time it takes for a pickup to respawn after a player picked it up.

Syntax
------

``` lua
bool setPickupRespawnInterval ( pickup thePickup, int ms )
```

### Required Arguments

-   **thePickup:** the pickup to set the respawn time of
-   **ms:** the new respawn time in ms

### Returns

Returns *true* if the new respawn time was set successfully, *false* otherwise.

Example
-------

This example adds 3000ms to the current pickup respawn time.

``` lua
addEventHandler("onPickUpHit",root,function(player)
    interval = getPickupRespawnInterval(source)
    setPickupRespawnInterval(source,interval + 3000)
    outputChatBox("That pickup isn't going to be there until "..tostring(interval).." is done.",player)
end)
```

See Also
--------
