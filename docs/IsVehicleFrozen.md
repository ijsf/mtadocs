This function checks if a vehicle has been frozen.

Syntax
------

``` lua
bool isVehicleFrozen ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** the vehicle whose freeze status we want to check.

### Returns

-   Returns *true* if the vehicle is frozen, *false* if it isn't or if invalid arguments were passed.

Example
-------

<section name="Server" class="server" show="true">
This example binds the “p” key to a function to freeze/unfreeze the player's current vehicle.

``` lua
-- this function freezes or unfreezes the specified player's vehicle, if he's in one
function toggleFreezeStatus ( thePlayer )
    -- if he is in a vehicle,
    if isPlayerInVehicle ( thePlayer ) then
        -- get the vehicle element
        local playerVehicle = getPlayerOccupiedVehicle ( thePlayer )
        -- get the current freeze status
        local currentFreezeStatus = isVehicleFrozen ( playerVehicle )
        -- get the new freeze status (the opposite of the previous)
        local newFreezeStatus = not currentFreezeStatus
        -- set the new freeze status
        setVehicleFrozen ( playerVehicle, newFreezeStatus )
    end
end

-- now make this function available as key bind to all players.
-- first, get the list of players
local connectedPlayers = getElementsByType ( "player" )
-- for each one in it,
for i, aPlayer in ipairs(connectedPlayers) do
    -- bind the player's "p" key to the toggleFreezeStatus function
    bindKey ( aPlayer, "p", "down", "Toggle freeze status", toggleFreezeStatus )
end
```

</section>
See Also
--------
