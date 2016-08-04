This function sets the position of an element to the specified coordinates.

<div style="background: #FF7070; border: 3px solid #FF0000;">
**Attention:** Do not use this function to spawn a [player](/docs/player.md "wikilink"). It will cause problems with other functions like [warpPedIntoVehicle](/warpPedIntoVehicle.md "wikilink").
Use [spawnPlayer](/docs/spawnPlayer.md "wikilink") instead.

</div>
Syntax
------

``` lua
bool setElementPosition ( element theElement, float x, float y, float z [, bool warp = true ] )  
```

### Required Arguments

-   **theElement:** A valid [element](/docs/element.md "wikilink") to be moved.
-   **x:** The x coordinate of the destination.
-   **y:** The y coordinate of the destination.
-   **z:** The z coordinate of the destination.

### Optional Arguments

-   **warp:** teleports players, resetting any animations they were doing. Setting this to *false* preserves the current animation.

### Returns

Returns *true* if the function was successful, *false* otherwise.

Example
-------

<section name="Example 1" class="server" show="true">
This example adds a “setpos” command to console, which allows setting of a player's position.

``` lua
function consoleSetPlayerPosition ( source, commandName, posX, posY, posZ )
    setElementPosition ( source, posX, posY, posZ )
end
addCommandHandler ( "setpos", consoleSetPlayerPosition  )
```

</section>
<section name="Example 2" class="client" show="false">
This example adds a “setpos” command to console, which allows setting of the local player's position.

``` lua
function consoleSetPlayerPosition ( commandName, posX, posY, posZ )
    setElementPosition ( localPlayer, posX, posY, posZ )
end
addCommandHandler ( "setpos", consoleSetPlayerPosition  )
```

</section>
<section name="Example 3" class="server" show="false">
This example enables a player to type /warpto <playername> to warp to them. If the player being warped to is in a vehicle with a free passenger seat, it will warp into the vehicle.

``` lua
function consoleWarpTo ( sourcePlayer, commandName, player2nick )
    -- Make sure required parameters are set
    if ( not sourcePlayer or not player2nick ) then return end
    -- Setup the variables we will be using for teleportation
    local x, y, z, r, d = 0, 0, 0, 0, 2.5
    -- Grab the element identifier of the player we are trying to warp to
    local player2 = getPlayerFromNick ( player2nick )
    -- Make sure it exists!
    if ( player2 ) then
        -- Is the player we're warping to in a vehicle?
        if ( isPlayerInVehicle ( player2 ) ) then
            -- Indeed they are, let's get the vehicle information such as the vehicle element itself, and the seats it's got.
            local player2vehicle = getPlayerOccupiedVehicle ( player2 )
            local numseats = getVehicleMaxPassengers ( player2vehicle )
            local i = 0
            -- Loop over the seats to see if there's a free one
            while ( i < numseats ) do
                if ( getVehicleOccupant ( player2vehicle, i ) ) then
                    -- This seat isn't free, go ahead and check the next one
                    i = i + 1
                else
                    -- This seat is free, get out of the loop
                    break
                end
            end
            -- Check if 'i' is lower than the number of seats. If it is, it means it's the number of a free seat
            if ( i < numseats ) then
                -- Teleport the player into the seat
                warpPlayerIntoVehicle ( sourcePlayer, player2vehicle, i )
            else
                -- There are no free seats, tell the player that.
                outputChatBox ( "Sorry, the player's vehicle is full (" .. getVehicleName ( player2vehicle ) .. " " .. i .. "/" .. numseats .. ")", sourcePlayer )
            end
        else
            -- The player isn't in a vehicle, let's get the player's position and warp to them.
            x, y, z = getElementPosition ( player2 )
            r = getPlayerRotation ( player2 )
            -- Make sure we get interior data, they might be inside one!
            interior = getElementInterior ( player2 )
            dimension = getElementDimension ( player2 )
            -- Do some funky math to make sure that we dont teleport inside of them (get us both stuck inside each other)
            x = x - ( ( math.cos ( math.rad ( r + 90 ) ) ) * d )
            y = y - ( ( math.sin ( math.rad ( r + 90 ) ) ) * d )
            -- Set a few timers for setting interiors, dimensions and positions
            setTimer ( setElementInterior, 800, 1, sourcePlayer, interior )
            setTimer ( setElementDimension, 900, 1, sourcePlayer, dimension )
            setTimer ( setElementPosition, 1000, 1, sourcePlayer, x, y, z )
            setTimer ( setPlayerRotation, 1000, 1, sourcePlayer, r )
            -- Fade the camera to make it look nicer
            fadeCamera ( sourcePlayer, false, 1, 0, 0, 0 )
            -- Fade it back once it's all complete!
            setTimer ( fadeCamera, 1000, 1, sourcePlayer, true, 1 )
        end
    else
        -- No player by the specified name was found, tell the warper this.
        outputChatBox ( "No such player.", sourcePlayer )
    end
end
addCommandHandler ( "warpto", consoleWarpTo )
```

</section>
See Also
--------
