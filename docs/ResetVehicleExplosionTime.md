Resets the vehicle explosion time. This is the point in time at which the vehicle last exploded: at this time plus the vehicle's respawn delay, the vehicle is respawned. You can use this function to prevent the vehicle from respawning.

Syntax
------

``` lua
bool resetVehicleExplosionTime ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle you wish to reset the explosion time from.

### Returns

Returns *true* if the vehicle explosion time has been reset, *false* if it failed to reset the explosion time.

Example
-------

This example resets every vehicle's explosion time when the resource is stopped.

``` lua
function resetVehiclesExplosionTime ()
    local vehicles = getElementsByType ( "vehicle" ) -- Return all the vehicles in a table
        for k, vehicle in ipairs ( vehicles ) do -- For every vehicle do the following...
            resetVehicleExplosionTime ( vehicle ) -- Reset the vehicle's explosion time
        end
end
-- When this resource is stopped, trigger the resetVehiclesExplosionTime function (above).
addEventHandler ( "onResourceStop", getResourceRootElement(getThisResource()), resetVehiclesExplosionTime )
```

See Also
--------
