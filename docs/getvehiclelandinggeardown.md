This function is used to check whether a vehicle's landing gear is down or not. Only planes can be used with this function.

Syntax
------

``` lua
bool getVehicleLandingGearDown ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** the [vehicle](/docs/vehicle.md "wikilink") of which you wish to check the landing gear state.

### Returns

Returns *true* if landing gear is down, *false* if the landing gear is up.
Returns *nil* if the vehicle has no landing gear, or is invalid.

Example
-------

This function tells you to pull up the landing gear if you're in a Hydra with its landing gear down.

``` lua
function checkGear( thePlayer )
    local theVehicle = getPedOccupiedVehicle( thePlayer )    --Get the players vehicle
    if ( getElementModel(theVehicle) == 520 and getVehicleLandingGearDown( theVehicle ) == false ) then    --if the vehicle is a hydra, and the landing gear is up
        outputChatBox( "Pull up!", thePlayer )    --tell the player to pull up.
    end
end
```

See Also
--------

[ru:getVehicleLandingGearDown ](/docs/ru-getvehiclelandinggeardown_.md "wikilink")
