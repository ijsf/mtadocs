Returns the suspension damping strength of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetSuspensionDamping ( handling theHandling )
float handlingGetSuspensionDamping ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the suspension damping strength, *or*
-   **vehicleID:** the vehicle ID of which you want to get the suspension damping strength.

### Returns

If you specified a handling element, returns its suspension damping if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the suspension damping that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
