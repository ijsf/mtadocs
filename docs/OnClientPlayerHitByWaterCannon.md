This event is fired when a player is hit by a water cannon.

Parameters
----------

``` lua
player playerHit
```

-   **playerHit:** the player which got shot by the water cannon

Source
------

The source of this event is the vehicle who shot the water cannon.

Type
----

This event is a pre reaction event meaning it occurs before any game level reaction to the collision which include:

-   Players flying off
-   Players being knocked down

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), the Player will not be knocked down

Example
-------

<section class="client" name="Client" show="true">
This example outputs a message when you are hit by a water cannon

``` lua
addEventHandler("onClientPlayerHitByWaterCannon",getRootElement(),
    function(player)
        local driver = getVehicleOccupant(source)
        if isElement(driver) then
            outputChatBox(""..getPlayerName(player).." is hit by the cannon of "..getPlayerName(driver).."'s vehicle.")
        end
    end
)
```

</section>
Requirements
------------

See Also
--------

### Client player events

### Client event functions
