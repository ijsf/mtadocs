Returns the maximum velocity of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetMaxVelocity ( handling theHandling )
float handlingGetMaxVelocity ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the maximum velocity, *or*
-   **vehicleID:** the vehicle ID of which you want to get the maximum velocity.

### Returns

If you specified a handling element, returns its maximum velocity if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the maximum velocity that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
