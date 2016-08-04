This function sets the position (and rotation) the vehicle will respawn to.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/docs/vehicle.md "wikilink") you wish to change the respawn position of.
-   **x**: A floating point number representing the X coordinate on the map.
-   **y**: A floating point number representing the Y coordinate on the map.
-   **z**: A floating point number representing the Z coordinate on the map.

### Optional Arguments

-   **rx**: A floating point number representing the rotation about the X axis in Degrees.
-   **ry**: A floating point number representing the rotation about the Y axis in Degrees.
-   **rz**: A floating point number representing the rotation about the Z axis in Degrees.

Returns
-------

Returns *true* if the vehicle was found and edited, *false* otherwise.

Example
-------

This example creates a vehicle and changes its respawn position.

``` lua
local vehicle = createVehicle ( 400, 1, 1, 1 ) -- create us a new vehicle
if ( vehicle ) then
  setVehicleRespawnPosition ( vehicle, 10, 10, 10 ) -- tell the server to respawn the vehicle at position (10,10,10)
end
```

See Also
--------
