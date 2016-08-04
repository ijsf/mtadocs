Returns the number of gears of a handling element or vehicle ID.

Syntax
------

``` lua
int handlingGetNumberOfGears ( handling theHandling )
int handlingGetNumberOfGears ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the number of gears, *or*
-   **vehicleID:** the vehicle ID of which you want to get the number of gears.

### Returns

If you specified a handling element, returns its number of gears if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the number of gears that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
