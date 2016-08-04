Returns the suspension force level (strength of the springs) of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetSuspensionForceLevel ( handling theHandling )
float handlingGetSuspensionForceLevel ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the suspension force, *or*
-   **vehicleID:** the vehicle ID of which you want to get the suspension force.

### Returns

If you specified a handling element, returns its suspension force if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the suspension force that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
