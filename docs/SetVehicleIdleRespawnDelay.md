This function sets the time delay (in milliseconds) the vehicle will remain at its position while empty.

Syntax
------

``` lua
bool setVehicleIdleRespawnDelay ( vehicle theVehicle, int timeDelay )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/docs/vehicle.md "wikilink") you wish to change the respawn delay of.
-   **timeDelay**: The number of milliseconds the vehicle will be allowed to remain unused until it respawns.

Returns
-------

Returns *true* if the vehicle was found and edited.

Example
-------

This example creates a vehicle and sets its respawn delay to 20 seconds.

``` lua
theVehicle = createVehicle ( 400, 1, 1, 1 )       -- create us a new vehicle
if ( theVehicle ) then
    toggleVehicleRespawn ( theVehicle, true ) -- enable vehicle respawn as it is necessary for the idle respawn to function
    setVehicleIdleRespawnDelay ( theVehicle, 20000 ) -- tell the server to respawn the vehicle 20 seconds after it's been left.
end
```

See Also
--------
