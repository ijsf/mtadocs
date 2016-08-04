This event is fired when a ped is hit by a water cannon.

Parameters
----------

``` lua
ped pedHit
```

-   **pedHit:** the ped which got shot by the water cannon

Source
------

The source of this event is the vehicle who shot the water cannon.

Type
----

This event is a pre reaction event meaning it occurs before any game level reaction to the collision which include:

-   Peds flying off
-   Peds being knocked down

Cancel effect
-------------

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the ped will not be knocked down

Example
-------

<section class="client" name="Client" show="true">
This example says who got hit by a water cannon.

``` lua
function outputPlayerHitByWater(thePed)
    if (getElementType(thePed) ~= "player") then
        return false -- This event is for peds and players but this example only wants players
    end
    local hitPed = getPlayerName(thePed)
    outputChatBox(hitPed.." got hit by a water cannon!", 255, 0, 0)
end
addEventHandler("onClientPedHitByWaterCannon", root, outputPlayerHitByWater)
 
```

</section>
Requirements
------------

See Also
--------

### Client ped events

### Client event functions
