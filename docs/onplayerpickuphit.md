This event is triggered when a [player](/docs/player.md "wikilink") hits a [pickup](/pickup.md "wikilink").

Parameters
----------

``` lua
pickup pickupHit, bool matchingDimension
```

-   **pickupHit**: The pickup the player hit
-   **matchingDimension**: Whether the player and the pickup he hit are in the same dimension

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that hit the pickup.

Cancel effect
-------------

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the player will not be able to pick up this pickup.

Example
-------

This example disables the use of armour pickups.

``` lua
function armourBlock(pickup,dimension)
    if (getPickupType(pickup) == 1) then -- If it's an armour pickup
        cancelEvent() -- Cancel the event
        outputChatBox("Armour pickups are disabled.",source,255,0,0)
    end
end
addEventHandler("onPlayerPickupHit",getRootElement(),armourBlock)
```
