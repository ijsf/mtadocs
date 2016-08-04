This function rotates a vehicle around a single point.

Syntax
------

``` lua
bool setVehicleRotation ( vehicle theVehicle, rx, ry, rz )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/vehicle.md "wikilink") that you wish to apply the warp to.
-   **x**: The x-axis rotation in degrees.
-   **y**: The y-axis rotation in degrees.
-   **z**: The z-axis rotation in degrees.

Returns
-------

Returns a boolean value *true* or *false* that tells you if it was successful or not.

Example
-------

``` lua
local newcar = createVehicle ( 520, 1024, 1024, 1024 ) 
if setVehicleRotation ( newcar, 0, 0, 270 ) then
    outputChatBox ( "Rotation change successful." )
end
```

See Also
--------
