This function sets the time delay (in milliseconds) the vehicle will remain wrecked before respawning.

Syntax
------

``` lua
bool setVehicleRespawnDelay ( vehicle theVehicle, int timeDelay )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/vehicle.md "wikilink") you wish to change the respawn delay of.
-   **timeDelay**: The amount of milliseconds to delay.

Returns
-------

Returns *true* if the vehicle was found and edited.

Example
-------

This example creates a vehicle and makes it so that it will respawn at its original position 20 seconds after it has blown up.

``` lua
newvehicle = createVehicle ( 400, 1, 1, 1 )       -- create us a new vehicle
if ( newvehicle ) then
    toggleVehicleRespawn ( newvehicle, true )     -- enable vehicle respawn
    setVehicleRespawnDelay ( newvehicle, 20000 )  -- tell the server to respawn the vehicle 20 seconds after it's blown
end
```

See Also
--------
