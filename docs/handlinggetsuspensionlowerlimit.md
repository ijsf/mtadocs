Returns the suspension lower limit of a handling element or vehicle ID (how low the wheels can go).

Syntax
------

``` lua
float handlingGetSuspensionLowerLimit ( handling theHandling )
float handlingGetSuspensionLowerLimit ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the suspension lower limit, *or*
-   **vehicleID:** the vehicle ID of which you want to get the suspension lower limit.

### Returns

If you specified a handling element, returns its suspension lower limit if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the suspension lower limit that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
