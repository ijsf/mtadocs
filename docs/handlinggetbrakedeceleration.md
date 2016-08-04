Returns the brake deceleration of a handling element or vehicle ID (how strongly the car can lock its tires while braking).

Syntax
------

``` lua
float handlingGetBrakeDeceleration ( handling theHandling )
float handlingGetBrakeDeceleration ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the brake deceleration, *or*
-   **vehicleID:** the vehicle ID of which you want to get the brake deceleration.

### Returns

If you specified a handling element, returns its brake deceleration if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the brake deceleration that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
