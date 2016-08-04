This function changes the paintjob on the specified vehicle.
See [paintjob](/Paintjob.md "wikilink") for list of supported vehicles.

Syntax
------

``` lua
bool setVehiclePaintjob ( vehicle theVehicle, int value )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/vehicle.md "wikilink") you wish to change the paintjob of.
-   **value**: A whole number representing the new paintjob id. Ranges from 0 up to 3.

Returns
-------

Returns *true* if the vehicle's paintjob was changed. Otherwise *false*.

Example
-------

This example will set the paintjob of a new sultan to '2'.

``` lua
newvehicle = createVehicle ( 560, 100, 100, 40 )  -- create the sultan
setVehiclePaintjob ( newvehicle, 2 )              -- change the paintjob
```

See Also
--------
