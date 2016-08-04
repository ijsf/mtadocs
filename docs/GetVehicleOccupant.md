This function gets the player sitting/trying to enter the specified vehicle.

Syntax
------

``` lua
player getVehicleOccupant ( vehicle theVehicle, [ int seat=0 ] )            
```

### Required Arguments

-   **theVehicle:** the [vehicle](/docs/vehicle.md "wikilink") of which you wish to retrieve the driver or a passenger.

### Optional Arguments

-   **seat:** the seat where the player is sitting (0 for driver, 1+ for passengers).

### Returns

Returns the [player](/docs/player.md "wikilink") sitting in the vehicle, or *false* if the seat is unoccupied or doesn't exist.

Example
-------

This example announces the driver of a certain vehicle whenever it is damaged:

``` lua
function onStolenVehicleDamage ( loss )
    local driver = getVehicleOccupant ( source ) -- get the player sitting in seat 0
    if ( driver ) then -- if the driver exists, display a message
        outputChatBox ( getPlayerName ( driver ) .. " is wrecking the vehicle he stole!" )
    end
end
addEventHandler ( "onVehicleDamage", stolenVehicle, onStolenVehicleDamage )
```

See Also
--------
