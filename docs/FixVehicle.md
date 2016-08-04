This function will set a [vehicle](/vehicle.md "wikilink")'s health to full and fix its damage model. If you wish to only change the vehicle's health, without affecting its damage model, use [setElementHealth](/setElementHealth.md "wikilink").

Syntax
------

``` lua
bool fixVehicle ( vehicle theVehicle )             
```

### Required Arguments

-   **theVehicle:** the vehicle you wish to fix

### Returns

Returns *true* if the vehicle was fixed, *false* if **theVehicle** is invalid.

Example
-------

This example fixes all the vehicles that exist in the map.

``` lua
-- Retrieve a table containing all the vehicles that exist
vehicles = getElementsByType ( "vehicle" )
-- Loop through the list, storing the vehicle from the table in the variable vehicleValue
for vehicleKey, vehicleValue in ipairs(vehicles) do
    -- fix the vehicle
    fixVehicle ( vehicleValue )
end
```

See Also
--------
