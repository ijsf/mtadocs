Sets the angular velocity of a vehicle. Basically applies a spin to it.

Syntax
------

``` lua
bool setVehicleTurnVelocity ( vehicle theVehicle, float rx, float ry, float rz )           
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") to apply the spin to.
-   **rx:** velocity around the X axis
-   **ry:** velocity around the Y axis
-   **rz:** velocity around the Z axis

### Returns

Returns *true* if it was succesful, *false* otherwise.

Example
-------

``` lua
function onColShapeHit ( thePlayer, matchingDimension )
    -- When a player hits the collision shape, check if he's in a vehicle
    local playerVehicle = getPedOccupiedVehicle ( thePlayer )
    if playerVehicle ~= false then
        -- If so, give it a spin
        setVehicleTurnVelocity ( playerVehicle, 0, 0, 20 )
    end
end
addEventHandler ( "onColShapeHit", getRootElement ( ), onColShapeHit )
```

See Also
--------
