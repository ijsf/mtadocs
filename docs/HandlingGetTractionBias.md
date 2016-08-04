Returns the traction bias of a handling element or vehicle ID. This determines how the grip is distributed over the front and back tires.

Syntax
------

``` lua
float handlingGetTractionBias ( handling theHandling )
float handlingGetTractionBias ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the traction bias, *or*
-   **vehicleID:** the vehicle ID of which you want to get the traction bias.

### Returns

If you specified a handling element, returns its traction bias if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the traction bias that currently applies to vehicles of that ID. Returns *false* in case of failure.

The traction bias is a number between 0 and 1. If it is 0, the back tires have all the grip and the front have none. If it is 1, only the front tires have grip. A value of 0.5 will give both tires the same amount of grip.

Example
-------

``` lua
--TODO
```

See Also
--------
