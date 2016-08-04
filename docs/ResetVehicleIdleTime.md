Resets the vehicle idle time

Syntax
------

``` lua
bool resetVehicleIdleTime ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle you wish to reset the idle time from.

### Returns

Returns *true* if the vehicle idle time has been reset, *false* if it failed to reset the idle time.

Example
-------

This example resets every vehicle's idle time when the resource is stopped.

``` lua
function resetVehiclesIdleTime ()
    local vehicles = getElementsByType ( "vehicle" ) -- Return all the vehicles in a table
        for k, vehicle in ipairs ( vehicles ) do -- For every vehicle do the following...
            resetVehicleIdleTime ( vehicle ) -- Reset the vehicle's idle time
        end
end
-- When this resource is stopped, trigger the resetVehiclesIdleTime function (above).
addEventHandler ( "onResourceStop", getResourceRootElement(getThisResource()), resetVehiclesIdleTime )
```

See Also
--------
