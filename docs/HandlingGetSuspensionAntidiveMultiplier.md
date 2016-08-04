Returns the suspension antidive multiplier of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetSuspensionAntidiveMultiplier ( handling theHandling )
float handlingGetSuspensionAntidiveMultiplier ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the suspension antidive multiplier, *or*
-   **vehicleID:** the vehicle ID of which you want to get the suspension antidive multiplier.

### Returns

If you specified a handling element, returns its suspension antidive multiplier if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the antidive multiplier that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
