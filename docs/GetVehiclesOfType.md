This function scans through all the current vehicles and returns the ones matching the given model.

Syntax
------

``` lua
table getVehiclesOfType ( int model )
```

### Required Arguments

-   **model**: The model of vehicles you want.

### Returns

Returns a table of existing vehicles matching the specified model.

Example
-------

This example finds all landstalkers on the map and moves them 5 units to the left.

``` lua
-- Find all the vehicles with the model 400 (landstalker)
vehicles = getVehiclesOfType ( 400 )
-- Loop through the vehicle list
for vehicleKey, vehicleValue in ipairs ( vehicles ) do
    -- Get the vehicle's position
        x, y, z = getElementPosition ( vehicleValue )
        -- Move the vehicle to the left
        setElementPosition ( vehicleValue, x - 5, y, z )
end
```

See Also
--------

[de:GetVehiclesOfType](/de:GetVehiclesOfType.md "wikilink")
