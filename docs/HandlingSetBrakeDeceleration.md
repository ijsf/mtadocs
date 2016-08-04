Sets the brake deceleration of a handling element. This determines how strongly a vehicle can lock its wheels when braking. High values will allow cars to immediately lock their wheels and cause skidding. Low values will merely slow down the wheels.

Syntax
------

``` lua
bool handlingSetBrakeDeceleration ( handling theHandling, float deceleration )
```

### Required Arguments

-   **theHandling:** the handling of which you want to change the brake deceleration.
-   **deceleration:** the brake decelertion to set.

### Returns

Returns *true* on success, *false* in case of failure.

Example
-------

Select a player and damage its vehicle's brakes

``` lua
function damageBreaks()
    local player = getPlayerFromName("David") -- get a player
    local vehicle = getPedOccupiedVehicle(player) -- get the vehicle David is in
    handlingSetBrakeDeceleration(vehicle, 0.08) -- reduce brake's strength
    outputChatBox("Your brakes are damaged. Drive careful!", player, 255, 0, 0)
end
```

See Also
--------
