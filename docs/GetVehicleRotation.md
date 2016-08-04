This function gets the rotation of a vehicle along the X, Y, and Z axes in degrees.

*Note: rotation Z returns value in CCW (counter-clock wise). So 3 o'clock is not 90 degrees, it's actually 270 degrees and 9 o'clock is not 270 degrees, it's 90 degrees. **To fix this use: rotZ = (360-rotZ)***

Syntax
------

``` lua
float float float getVehicleRotation ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/vehicle.md "wikilink") whose rotation you want to retrieve.

### Returns

Returns three *floats* indicating the X, Y, and Z rotations of the vehicle in degrees, or *false* if the specified vehicle does not exist.

Example
-------

This example creates a vehicle and gets its rotation:

``` lua
local newHydra = createVehicle ( 520, 1024, 1024, 1024 ) -- create a Hydra
local rx, ry, rz = getVehicleRotation ( newHydra ) -- get the vehicle's x, y and z rotations and store them in rx, ry, and rz
outputChatBox ( "Current rotation: " .. rx .. " " .. ry .. " " .. rz ) -- output the rotations
```

See Also
--------
