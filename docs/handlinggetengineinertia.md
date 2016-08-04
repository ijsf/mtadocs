Returns the engine interia of a handling element or vehicle ID. A higher inertia makes a slower car.

Syntax
------

``` lua
float handlingGetEngineInertia ( handling theHandling )
float handlingGetEngineInertia ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the inertia, *or*
-   **vehicleID:** the vehicle ID of which you want to get the inertia.

### Returns

If you specified a handling element, returns its inertia if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the inertia that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
