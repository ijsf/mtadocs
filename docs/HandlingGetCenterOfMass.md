Returns the center of mass of a handling element or vehicle ID. This is a 3D vector relative to the center of the mesh.

Syntax
------

``` lua
float float float handlingGetCenterOfMass ( handling theHandling )
float float float handlingGetCenterOfMass ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you wish to get the center of mass, *or*
-   **int vehicleID:** the vehicle ID of which you want to get the center of mass.

### Returns

If you specified a handling element, returns the x, y and z components of the center of mass vector of the handling element if it is set, or *nil* if not. If you specified a vehicle ID, returns the x, y, and z components of the center of mass that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
