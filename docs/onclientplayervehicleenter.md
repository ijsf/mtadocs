This event is fired when a player enters a vehicle.

Parameters
----------

``` lua
vehicle theVehicle, int seat
```

-   **theVehicle:** the vehicle that the player entered
-   **seat:** the seat that the player now is on. Driver's seat = 0, higher numbers are passenger seats.

Source
------

The source of this event is the player that entered the vehicle.

Example
-------

This will check if the car you entered is a Banshee or not.

``` lua
function checkVehicles()
    local theVehicle = getPedOccupiedVehicle(source)
    if (getVehicleName(theVehicle)) == "Banshee" then
        outputChatBox("You entered a Banshee!")
    else
        outputChatBox("This isn't a Banshee!")
    end
end
addEventHandler("onClientPlayerVehicleEnter",getRootElement(),checkVehicles)
```

See Also
--------

### Client player events

### Client event functions
