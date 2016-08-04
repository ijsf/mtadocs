This event is triggered when a player starts exiting a vehicle. Once the exiting animation completes, [onClientVehicleExit](/docs/onClientVehicleExit.md "wikilink") is triggered.

Parameters
----------

``` lua
player thePlayer, int seat, int door
```

-   **thePlayer:** the player who started exiting the vehicle.
-   **seat:** the number of the seat that the player was sitting on.

Source
------

The source of this event is the vehicle that the player started to exit.

Example
-------

This example outputs to the player that he's leaving the drivers seat.

``` lua
function exitingVehicle(player, seat, door)
    if (seat==0) and (door==0) then
        outputChatBox("You are leaving the drivers seat.")
    end
end
addEventHandler("onClientVehicleStartExit", getRootElement(), exitingVehicle)
```

See Also
--------

### Client vehicle events

### Client event functions

[es:onClientVehicleStartExit](/docs/es:onClientVehicleStartExit.md "wikilink")
