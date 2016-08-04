This event gets fired when a player enters a vehicle.

Parameters
----------

``` lua
player thePlayer, int seat
```

-   **thePlayer:** the player that entered the vehicle
-   **seat:** the number of the seat that the player is now sitting on. 0 = driver, higher numbers are passenger seats.

Source
------

The source of the event is the vehicle that the player entered.

Example
-------

This code updates a GUI label with the name of the vehicle the local player is in.

``` lua
lblVehicle = guiCreateLabel(10, 200, 150, 20, "Currently on foot", false)
addEventHandler("onClientVehicleEnter", getRootElement(),
    function(thePlayer, seat)
        if thePlayer == getLocalPlayer() then
            guiSetText(lblVehicle, "Currently in a " .. getVehicleName(source))
        end
    end
)
addEventHandler("onClientVehicleExit", getRootElement(),
    function(thePlayer, seat)
        if thePlayer == getLocalPlayer() then
            guiSetText(lblVehicle, "Currently on foot")
        end
    end
)
```

See Also
--------

### Client vehicle events

### Client event functions

[es:onClientVehicleEnter](/docs/es:onclientvehicleenter.md "wikilink")
