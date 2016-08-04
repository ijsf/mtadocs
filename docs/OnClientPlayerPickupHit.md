This event triggers whenever a player hits a pickup locally.

Parameters
----------

``` lua
pickup thePickup, bool matchingDimension
```

-   **thePickup:** the pickup that was hit.
-   **matchingDimension:** *true* if thePickup is in the same dimension as the player, *false* otherwise.

Source
------

The source of this event is the player that hit the pickup.

Example
-------

This example outputs a message whenever the local player hits a pickup.

``` lua
local function clientPlayerPickupHit(thePickup, matchingDimension)
    outputChatBox("* You have hit a pickup!", 255, 0, 0)
end
addEventHandler("onClientPlayerPickupHit", localPlayer, clientPlayerPickupHit)
```

Requirements
------------

See Also
--------

### Client pickup events

### Client player events

### Client event functions
