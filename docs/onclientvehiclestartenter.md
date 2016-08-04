This event is triggered when a player starts entering a vehicle. Once the entering animation completes, [onClientVehicleEnter](/docs/onclientvehicleenter.md "wikilink") is triggered.

Parameters
----------

-   **thePlayer:** the player that just started entering a vehicle.
-   **seat:** the number of the seat he is going to sit on.

Source
------

The source of this event is the vehicle the player is entering.

Example
-------

This example outputs if the player is sitting in the drivers seat. (TESTED!)

``` lua
addEventHandler("onClientVehicleStartEnter",root,function(player,seat,door)
    if(seat==0)and(door==0)then
        outputChatBox("You are going to sit in the drivers seat.",player)
    end
end)
```

See Also
--------

### Client vehicle events

### Client event functions

[es:onClientVehicleStartEnter](/docs/es-onclientvehiclestartenter.md "wikilink")
