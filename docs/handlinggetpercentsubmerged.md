Returns the percentage (a value between 0 and 100) that a vehicle gets submerged when it lands on the surface of water.

Syntax
------

``` lua
float handlingGetPercentSubmerged ( handling theHandling )
float handlingGetPercentSubmerged ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the submersion percentage, *or*
-   **vehicleID:** the vehicle ID of which you want to get the submersion percentage.

### Returns

If you specified a handling element, returns its submersion percentage if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the current submersion percentage for vehicles of that ID. Returns *false* in case of failure.

Example
-------

See Also
--------
