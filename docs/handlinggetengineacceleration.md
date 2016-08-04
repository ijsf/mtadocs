Returns the acceleration of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetEngineAcceleration ( handling theHandling )
float handlingGetEngineAcceleration ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the acceleration, *or*
-   **vehicleID:** the vehicle ID of which you want to get the acceleration.

### Returns

If you specified a handling element, returns its acceleration if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the acceleration that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
