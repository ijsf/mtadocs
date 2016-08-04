This event is triggered when a player is standing on a pickup while not being in a vehicle.

Parameters
----------

``` lua
pickup thePickupToUse
```

-   **thePickupToUse**: The pickup the player is standing on and is about to pick up.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that is standing on a pickup.

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), the player will not be able to pick up this pickup.

Example
-------

This example outputs to the player that's using the pick that the pickup is either available/unavailable.

``` lua
addEventHandler("onPlayerPickupUse",root,function(pickup)
    if(isPickupSpawned(pickup))then
        outputChatBox("The pickup your using is now available to use pick up again.",source)
    else
        outputChatBox("This pickup might be the last pickup to use ever again.",source)
    end
end)
```
