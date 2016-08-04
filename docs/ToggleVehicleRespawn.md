This function toggles whether or not the vehicle will be respawned after blown or idle.

Syntax
------

``` lua
bool toggleVehicleRespawn ( vehicle theVehicle, bool Respawn )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/vehicle.md "wikilink") you wish to toggle the respawning of.
-   **Respawn**: A boolean determining if the vehicle will respawn or not.

Returns
-------

Returns *true* if the vehicle was found and edited.

Example
-------

This example defines a console command that will disable respawning for the vehicle that the player is currently in.

``` lua
function doNotRespawn ( thePlayer )
    local theVehicle = getPlayerOccupiedVehicle ( thePlayer )
    if ( theVehicle ) then
        toggleVehicleRespawn ( theVehicle, false ) -- tell the server not to respawn this vehicle
    end
end
addCommandHandler("donotrespawn", doNotRespawn)
```

See Also
--------
