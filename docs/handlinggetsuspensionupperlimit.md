Returns the suspension upper limit of a handling element or vehicle ID (how high the wheels can go).

Syntax
------

``` lua
float handlingGetSuspensionUpperLimit ( handling theHandling )
float handlingGetSuspensionUpperLimit ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the suspension upper limit, *or*
-   **vehicleID:** the vehicle ID of which you want to get the suspension upper limit.

### Returns

If you specified a handling element, returns its suspension upper limit if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the suspension upper limit that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
