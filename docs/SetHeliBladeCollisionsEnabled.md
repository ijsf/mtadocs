This function changes the state of the helicopter blades collisions on the specified vehicle.

Syntax
------

``` lua
bool setHeliBladeCollisionsEnabled ( vehicle theVehicle, bool collisions )
```

### Required Arguments

-   **theVehicle:** The helicopter that will have the blades collisions set.
-   **collisions:** The state of the helicopter blades collisions.

### Returns

Returns *true* if the collisions are set for the specified vehicle, *false* if the collisions can't be set for the specified vehicle, if the vehicle is not a helicopter or if invalid arguments are specified.

Example
-------

<section name="Client" class="client" show="true">
This example disables blades collisions when a player enters a helicopter as a driver.

``` lua
function onVehicleEnter ( thePlayer, seat, jacked )
    --If the player entered a helicopter
    if ( getVehicleType ( source ) == "Helicopter" ) then
        --If the player entered as a driver
        if ( seat == 0 ) then
            -- Turn off collisions
            setHeliBladeCollisionsEnabled ( source, false )
        end
    end
end
addEventHandler ( "onClientVehicleEnter", root, onVehicleEnter )
```

</section>
See Also
--------
