Returns the ABS (Anti-lock Braking System) setting of a handling element or vehicle ID.

Syntax
------

``` lua
bool handlingGetABS ( handling theHandling )
bool handlingGetABS ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the ABS setting, *or*
-   **vehicleID:** the vehicle ID of which you want to get the ABS setting.

### Returns

If you specified a handling element, returns its ABS setting if one is set (*true* if ABS is active, *false* if not), or *nil* otherwise. If you specified a vehicle ID, returns the ABS setting that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
