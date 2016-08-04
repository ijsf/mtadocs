Spawns a vehicle at any given position and rotation

Syntax
------

``` lua
bool spawnVehicle ( vehicle theVehicle, float x, float y, float z [, float rx, float ry, float rz ] )
```

### Required Arguments

-   **theVehicle:** The vehicle you wish to spawn
-   **x:** The x position you wish to spawn the vehicle at
-   **y:** The x position you wish to spawn the vehicle at
-   **z:** The x position you wish to spawn the vehicle at

### Optional Arguments

-   **rx:** The x rotation you wish to spawn the vehicle at
-   **ry:** The y rotation you wish to spawn the vehicle at
-   **rz:** The z rotation you wish to spawn the vehicle at

### Returns

Returns *true* if the vehicle spawned successfully, *false* if the passed argument does not exist or is not a vehicle.

Example
-------

<section name="Server" class="server" show="true">
With this feature, we spawn vehicle

``` lua
function myCommandHandler(thePlayer, command)
    local x, y, z = getElementPosition(thePlayer)
    local RaceVehicle = createVehicle ( 411, 0, 0, 0 ) 
    local spawnVeh = spawnVehicle ( RaceVehicle, x+3, y+3, z )  
    if spawnVeh then    outputChatBox("Vehicle was spawned", thePlayer) else    outputChatBox("Error",thePlayer)    end
end

addCommandHandler("spawnvehicle", myCommandHandler)
```

</section>
Related scripting functions
---------------------------
