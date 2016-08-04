Returns the engine type of a handling element or vehicle ID - more specifically, what type of fuel it uses.

Syntax
------

``` lua
string handlingGetEngineType ( handling theHandling )
string handlingGetEngineType ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the engine type, *or*
-   **vehicleID:** the vehicle ID of which you want to get the engine type.

### Returns

If you specified a handling element, returns its engine type if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the engine type that currently applies to vehicles of that ID. Returns *false* in case of failure.

Possible engine types are:

-   **diesel**
-   **electric**
-   **petrol**

Example
-------

``` lua
--TODO
```

See Also
--------
