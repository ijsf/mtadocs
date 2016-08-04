This function checks if a pickup is currently spawned (is visible and can be picked up) or not (a player picked it up recently).

Syntax
------

``` lua
bool isPickupSpawned ( pickup thePickup )
```

### Required Arguments

-   **thePickup:** the pickup you want to check.

### Returns

Returns *true* if the pickup is spawned, *false* if it's not spawned or an invalid pickup was specified.

Example
-------

This example outputs to the player that' using the pick that the pickup is either available/unavailable.

``` lua
addEventHandler("onPickupUse",root,function(player)
    if(isPickupSpawned(source))then
        outputChatBox("The pickup your using is now available to use pick up again.",player)
    else
        outputChatBox("This pickup might be the last pickup to use ever again.",player)
    end
end)
```

See Also
--------
