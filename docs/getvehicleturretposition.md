This function gets the position of a vehicle's turret, if it has one. Vehicles with turrets include firetrucks and tanks.

Syntax
------

``` lua
float, float getVehicleTurretPosition ( vehicle turretVehicle )
```

### Required Arguments

-   **turretVehicle**: The [vehicle](/docs/vehicle.md "wikilink") whose turret position you want to retrieve. This should be a vehicle with a turret.

### Returns

Returns two [floats](/docs/float.md "wikilink") for the X (horizontal) and Y (vertical) axis rotation respectively. These values are in radians. The function will return *0, 0* if the vehicle is not a vehicle with a turret.

Example
-------

``` lua
-- Find all the vehicles, and store them in a vehicles variable
local vehicles = getElementsByType ( "vehicle" )
-- Loop through the vehicle list
for vehicleKey, vehicleValue in ipairs(vehicles) do
    -- Get the vehicle's turret position
    local x, y = getVehicleTurretPosition ( vehicleValue ) 
    -- Convert the positions to degrees, as that's much more useful if you'd want to output it
    x = math.deg ( x )
    y = math.deg ( y )
    -- Get the vehicle's name
    local vehicleName = getVehicleName ( vehicleValue )
    -- Tell everyone in the F8 console the turret's position
    outputConsole ( vehicleName .. "'s turret rotation: " .. x .. ", " .. y .. "." )    
end
```

See Also
--------
