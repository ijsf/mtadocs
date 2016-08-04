Please use [setElementFrozen](/docs/setElementFrozen.md "wikilink")

This function freezes a vehicle (stops it in its position and disables movement) or unfreezes it.

Syntax
------

<section name="Server and Client" class="both" show="true">
``` lua
bool setVehicleFrozen ( vehicle theVehicle, bool freezeStatus )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") whose freeze status we want to change.
-   **freezeStatus:** A boolean denoting whether we want to freeze (*true*) or unfreeze (*false*) it.

### Returns

Returns *true* if the vehicle was frozen, *false* if it wasn't or if invalid arguments are passed.

</section>
Example
-------

<section name="Serverside example" class="server" show="true">
This example binds the “p” key to a function to freeze/unfreeze the player's current vehicle.

``` lua
-- This function freezes the specified player's vehicle, if he's in one
function toggleFreezeStatus ( thePlayer )
    -- if he is in a vehicle,
    if isPlayerInVehicle ( thePlayer ) then
        -- get the vehicle element
        local playerVehicle = getPlayerOccupiedVehicle ( thePlayer )
        -- get the current freeze status
        local currentFreezeStatus = isVehicleFrozen ( playerVehicle )
        -- get the new freeze status (the opposite of the previous state)
        local newFreezeStatus = not currentFreezeStatus
        -- set the new freeze status
        setVehicleFrozen ( playerVehicle, newFreezeStatus )
    end
end

-- now bind a key to this function for all players.
-- first get a list of all players
local connectedPlayers = getElementsByType ( "player" )
-- then, for each player,
for i, aPlayer in ipairs(connectedPlayers) do
    -- bind the player's "p" key to the toggleFreezeStatus function
    bindKey ( aPlayer, "p", "down", "Toggle freeze status", toggleFreezeStatus )
end
```

</section>
See Also
--------
