Retrieves the current gravity vector of a vehicle. This is the direction in which the vehicle falls, also the cameras of any passengers will be rotated to match it.

Syntax
------

``` lua
float float float getVehicleGravity ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** the vehicle to retrieve the gravity vector of.

### Returns

Returns the x, y and z components of the gravity vector if successful, *false* otherwise.

See Also
--------
