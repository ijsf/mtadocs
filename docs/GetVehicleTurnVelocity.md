This function is used to retrieve a vehicle's turning velocity for each axis.

Syntax
------

``` lua
float float float getVehicleTurnVelocity ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") you wish to get the turning velocities of.

### Returns

Returns 3 *floats* that represent the vehicle's turning velocity on the x, y and z axis or *false* if wrong arguments were passed.

### Example

<section name="Server" class="server" show="true">
This example shows the current turn velocity of the vehicle that you're in.

``` lua
addCommandHandler("geturnvelocity", function(player)
    if not isPedInVehicle(player) then return end
    local veh = getPedOccupiedVehicle(player)
    local vx, vy, vz = getVehicleTurnVelocity(veh)
    outputChatBox("Vehicle's turn velocity is: X: "..vx.." Y: "..vy.." Z: "..vz, player, 0, 255, 0, false)
end)
```

</section>
See Also
--------
