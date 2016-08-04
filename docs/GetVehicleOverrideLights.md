This function is used to find out the current state of the override-lights setting of a vehicle.

Syntax
------

``` lua
int getVehicleOverrideLights ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle**: the [vehicle](/docs/vehicle.md "wikilink") you wish to retrieve the override lights setting of.

### Returns

Returns an integer value: 0 (No override), 1 (Force off) or 2 (Force on).

Example
-------

This example will toggle the car lights on and off for a player's vehicle

``` lua
function vehicleLights ( source )
    local theVehicle = getPlayerOccupiedVehicle ( source )        -- get the player's vehicle
    if ( theVehicle ) then                                        -- if he was in one
        if ( getVehicleOverrideLights ( theVehicle ) ~= 2 ) then  -- if the current state isnt 'force on'
            setVehicleOverrideLights ( theVehicle, 2 )            -- force the lights on
        else
            setVehicleOverrideLights ( theVehicle, 1 )            -- otherwise, force the lights off
        end
    end
end
addCommandHandler ( "vehiclelights", vehicleLights )
```

See Also
--------
