This function returns the current state of the specified light on the vehicle.

Syntax
------

``` lua
int getVehicleLightState ( vehicle theVehicle, int light )
```

Required Arguments
------------------

-   **theVehicle:** the [vehicle](/docs/vehicle.md "wikilink") that you wish to know the light state of.
-   **light:** the whole number between 0 and 3

Returns
-------

Returns 0 (working) or 1 (broken)

Example
-------

``` lua
newcar = createVehicle ( 520, 1024, 1024, 1024 )
state = getVehicleLightState ( newcar, 0 )
outputChatBox ( "The front-left light state on this car: " .. state )
```

See Also
--------
