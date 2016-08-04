This will tell you if a vehicle's petrol tank is explodable.

Syntax
------

``` lua
bool isVehicleFuelTankExplodable ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") that you want to obtain the fuel tank status of.

### Returns

Returns *true* if the specified vehicle is valid and its fuel tank is explodable, *false* otherwise.

Example
-------

This example creates a vehicle, then displays if it fuel tank is explodable or not in the chatbox.

``` lua
newcar = createVehicle ( 520, 1024, 1024, 1024 )
if ( isVehicleFuelTankExplodable ( newcar ) ) then
    outputChatBox ( "Vehicle's tank is explodable" )
else
    outputChatBox ( "Vehicle's tank is not explodable" )
end
```

Example 2
---------

This example toggles vehicle fuel tank explodable when the player type *fueltank* in the chat.

``` lua
function toggleFuelTankExplodable(playerSource)
vehicle = getPedOccupiedVehicle(playerSource)
    if vehicle then
        if isVehicleFuelTankExplodable(vehicle) then
            setVehicleFuelTankExplodable(vehicle, false)
        else
            setVehicleFuelTankExplodable(vehicle, true)
        end
    else
        outputChatBox("You are not in a vehicle.", playerSource, 220, 0, 0)
    end
end
addCommandHandler("fueltank", toggleFuelTankExplodable)
```

See Also
--------
