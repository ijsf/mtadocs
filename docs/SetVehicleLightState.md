This function sets the state of the light on the vehicle.

Syntax
------

``` lua
bool setVehicleLightState ( vehicle theVehicle, int light, int state )
```

Required Arguments
------------------

-   **theVehicle:** A handle to the [vehicle](/vehicle.md "wikilink") that you wish to change the light state of.
-   **light:** A whole number determining the individual light. (0 - 3)
-   **state:** A whole number determining the new state of the light. *0* represents normal lights, and *1* represents broken lights.

### Returns

Returns *true* if the light state was set successfully, *false* if invalid arguments were passed to the function.

Example
-------

``` lua
newcar = createVehicle ( 520, 1024, 1024, 1024 )   -- create a new vehicle
state = setVehicleLightState ( newcar, 0,  1 )     -- break the left front light
```

See Also
--------
