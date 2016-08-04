Returns the high speed suspension damping strength of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetSuspensionHighSpeedDamping ( handling theHandling )
float handlingGetSuspensionHighSpeedDamping ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the high speed suspension damping strength, *or*
-   **vehicleID:** the vehicle ID of which you want to get the high speed suspension damping strength.

### Returns

If you specified a handling element, returns its high speed suspension damping if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the high speed suspension damping that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
