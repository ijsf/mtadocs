Returns the steering lock of a handling element or vehicle ID (how strongly the car can steer).

Syntax
------

``` lua
float handlingGetSteeringLock ( handling theHandling )
float handlingGetSteeringLock ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the steering lock, *or*
-   **vehicleID:** the vehicle ID of which you want to get the steering lock.

### Returns

If you specified a handling element, returns its steering lock if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the steering lock that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
--TODO
```

See Also
--------
