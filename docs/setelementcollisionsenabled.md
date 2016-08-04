This function can disable or enable an element's collisions. An element without collisions does not interact with the physical environment and remains static.

Syntax
------

``` lua
bool setElementCollisionsEnabled ( element theElement, bool enabled ) 
```

### Required Arguments

-   **theElement:** The element you wish to set the collisions of
-   **enabled:** A boolean to indicate whether collisions are enabled (*true*) or disabled (*false*)

### Returns

Returns *true* if the collisions were set succesfully, *false* otherwise.

Example
-------

This example disables collisions for all vehicles within a certain radius of a player:

``` lua
function disableVehicleCollisionsNearPlayer(thePlayer, maxDistance)
    local playerX, playerY, playerZ = getElementPosition(thePlayer)
    local vehicles = getElementsByType("vehicle")
    for k,v in ipairs(vehicles) do
        local vehicleX, vehicleY, vehicleZ = getElementPosition(v)
        -- get the distance between the player and the vehicle:
        local distance = getDistanceBetweenPoints3D(vehicleX, vehicleY, vehicleZ, playerX, playerY, playerZ)
        if (distance <= maxDistance) then
            -- disable collisions for the vehicle
            setElementCollisionsEnabled(v, false)
        end
    end
end
```

See Also
--------
