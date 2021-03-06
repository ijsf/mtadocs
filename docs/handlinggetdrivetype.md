Returns the drive type of a handling element or vehicle ID.

Syntax
------

``` lua
string handlingGetDriveType ( handling theHandling )
string handlingGetDriveType ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the drive type, *or*
-   **vehicleID:** the vehicle ID of which you want to get the drive type.

### Returns

If you specified a handling element, returns its drive type if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the drive type that currently applies to vehicles of that ID. Returns *false* in case of failure.

Possible drive types are:

-   **fwd:** car is front wheel driven
-   **rwd:** car is rear wheel driven
-   **awd:** car is all wheel driven

Example
-------

``` lua
--TODO
```

See Also
--------
