This function sets the position of a vehicle's turret, if it has one. This can be used to influence the turret's rotation, so it doesn't follow the camera. Vehicles with turrets include firetrucks and tanks.

Syntax
------

``` lua
bool setVehicleTurretPosition ( vehicle turretVehicle, float positionX, float positionY )
```

### Required Arguments

-   **turretVehicle**: The [vehicle](/vehicle.md "wikilink") whose turret position you want to retrieve. This should be a vehicle with a turret.
-   **positionX**: The horizontal position of the turret. In radians
-   **positionY**: The vertical position of the turret. In radians

### Returns

Returns a *true* if a valid vehicle element and valid positions were passed, *false* otherwise.

Example
-------

This example will force vehicle turrets to aim straight forwards.

``` lua
-- Find all the vehicles, and store them in a vehicles variable
local vehicles = getElementsByType ( "vehicle" )
-- Loop through the vehicle list
for vehicleKey, vehicleValue in ipairs(vehicles) do
    -- Set the turret to aim straight forwards
    setVehicleTurretPosition ( vehicleValue, 0, 0 )
end
```

See Also
--------
