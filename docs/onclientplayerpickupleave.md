This event triggers whenever a player leaves pickup locally.

Parameters
----------

``` lua
pickup thePickup, bool matchingDimension
```

-   **thePickup:** the pickup that was left.
-   **matchingDimension:** *true* if thePickup is in the same dimension as the player, *false* otherwise.

Source
------

The source of this event is the player that left the pickup.

Example
-------

This example outputs a message whenever the local player leaves a pickup.

``` lua
local function clientPlayerPickupLeave(thePickup, matchingDimension)
    outputChatBox("* You have left a pickup!", 255, 0, 0)
end
addEventHandler("onClientPlayerPickupLeave", localPlayer, clientPlayerPickupLeave)
```

Requirements
------------

See Also
--------

### Client pickup events

### Client player events

### Client event functions
