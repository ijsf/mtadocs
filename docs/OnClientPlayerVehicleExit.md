This event is triggered when a player exits a vehicle.

Parameters
----------

``` lua
vehicle theVehicle, int seat
```

-   **theVehicle:** the vehicle that the player exited.
-   **seat:** the number of the seat that the player was sitting on.

Source
------

The source of this event is the [player](/player.md "wikilink") that exited the vehicle.

Example
-------

This example outputs a chat box message with player's name and vehicle name when someone leave vehicle.

``` lua
addEventHandler("onClientPlayerVehicleExit", getRootElement(),

function (vehicle, seat)

local vehicleName = getVehicleName(vehicle)
outputChatBox("Player " .. getPlayerName(source) .. " has left the " .. vehicleName)

end)
```

See Also
--------

### Client player events

### Client event functions
