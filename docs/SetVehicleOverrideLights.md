This function changes the light overriding setting on a vehicle.

Syntax
------

``` lua
bool setVehicleOverrideLights ( vehicle theVehicle, int value )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/docs/vehicle.md "wikilink") you wish to change the override lights setting of.
-   **value**: A whole number representing the state of the lights:
    -   **0**: No override, lights are set to default.
    -   **1**: Lights are forced off.
    -   **2**: Lights are forced on.

Returns
-------

Returns *true* if the vehicle's lights setting was changed. Otherwise *false*.

Example
-------

<section name="Example 1" class="server" show="true">
This example will toggle the car lights on and off for a player's vehicle by using a “vehiclelights” command.

``` lua
function consoleVehicleLights ( source )
    playerVehicle = getPedOccupiedVehicle ( source )                 -- get the player's vehicle
    if ( playerVehicle ) then                                        -- if he was in one
        if ( getVehicleOverrideLights ( playerVehicle ) ~= 2 ) then  -- if the current state isn't 'force on'
            setVehicleOverrideLights ( playerVehicle, 2 )            -- force the lights on
        else
            setVehicleOverrideLights ( playerVehicle, 1 )            -- otherwise, force the lights off
        end
    end
end
addCommandHandler ( "vehiclelights", consoleVehicleLights )
```

</section>
<section name="Example 2" class="client" show="true">
This example will toggle the car lights on and off for a player's vehicle by using a “vehiclelights” command.

``` lua
function consoleVehicleLights ()
    playerVehicle = getPedOccupiedVehicle ( getLocalPlayer() )       -- get the local player's vehicle
    if ( playerVehicle ) then                                        -- if he was in one
        if ( getVehicleOverrideLights ( playerVehicle ) ~= 2 ) then  -- if the current state isn't 'force on'
            setVehicleOverrideLights ( playerVehicle, 2 )            -- force the lights on
        else
            setVehicleOverrideLights ( playerVehicle, 1 )            -- otherwise, force the lights off
        end
    end
end
addCommandHandler ( "vehiclelights", consoleVehicleLights )
```

</section>
See Also
--------
