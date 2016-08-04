<lowercasetitle></lowercasetitle>

This function checks if a [vehicle](/vehicle.md "wikilink") is being occupied by a [ped](/ped.md "wikilink") or [player](/player.md "wikilink").

Syntax
------

``` lua
bool, ped/player isVehicleOccupied( element vehicle )
```

### Required Arguments

-   **vehicle**: The [vehicle](/vehicle.md "wikilink") you want to check if it's occupied or not.

### Returns

Returns *true* and the first occupant found if the vehicle is being occupied, *false* if it's empty or invalid.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function isVehicleOccupied(vehicle)
    assert(isElement(vehicle) and getElementType(vehicle) == "vehicle", "Bad argument @ isVehicleOccupied [expected vehicle, got " .. tostring(vehicle) .. "]")
    local _, occupant = next(getVehicleOccupants(vehicle))
    return occupant and true, occupant
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example creates an Infernus at the center of the map and adds a /respawninfernus command to respawn it if it's empty.

    local infernus = createVehicle(411, 0, 0, 20)
    setVehicleRespawnPosition(infernus, 0, 0, 20)

    function respawnCar(player)
        if not isVehicleOccupied(infernus) then
            respawnVehicle(infernus)
            outputChatBox("The Infernus has been respawned.", player, 0, 255, 0)
        else
            local _, ped = isVehicleOccupied(infernus)
            local ped = getElementType(ped) == "player" and ped or nil
            outputChatBox(((not ped) and "Someone" or getPlayerName(ped)) .. " is using the Infernus.", player, 255, 0, 0)
        end
    end
    addCommandHandler("respawninfernus", respawnCar)

</section>
See Also
--------
