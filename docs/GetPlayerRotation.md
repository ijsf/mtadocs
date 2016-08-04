This function returns the current rotation (in degrees) of a player around the Z axis. It's used with on-foot players: use [getVehicleRotation](/getVehicleRotation.md "wikilink") on the occupied [vehicle](/vehicle.md "wikilink") if the player is in one.

Syntax
------

``` lua
float getPlayerRotation ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: the [player](/player.md "wikilink") whose rotation you want to retrieve.

### Returns

Returns a *float* containing the player's rotation, or *false* if an invalid player (or one in a vehicle) was passed.

Example
-------

This code adds a *getrot* command to get the player's current rotation.

``` lua
function outputPlayerRotation ( sourcePlayer )
    -- if the command was triggered by an ingame player
    if ( sourcePlayer ) then
        -- if he is in a vehicle
        if isPlayerInVehicle ( sourcePlayer ) then
            -- store the vehicle element
            local playerVehicle = getPlayerOccupiedVehicle ( sourcePlayer )
            -- and output its rotation
            local x,y,z = getVehicleRotation ( playerVehicle )
            outputChatBox ( "Your vehicle's rotation is: " .. z, sourcePlayer )
        -- if he is on foot
        else
            -- output the player's rotation
            outputChatBox ( "Your rotation is: " .. getPlayerRotation ( sourcePlayer ), sourcePlayer )
        end
    end
end

-- register outputPlayerRotation as a handler for the getrot command
addCommandHandler ( "getrot", outputPlayerRotation )
```

See Also
--------
