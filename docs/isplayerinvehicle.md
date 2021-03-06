This function checks if a player is in a vehicle.

Syntax
------

``` lua
bool isPlayerInVehicle ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") element you are checking.

### Returns

Returns *true* if the player is inside a vehicle, *false* if he isn't or an invalid player was passed.

Example
-------

This code defines an *isinvehicle* command which tells a player whether another player is in a vehicle or not.

``` lua
-- we create our handler function, where sourcePlayer is the player who sent the command,
-- and checkedPlayerName is the player name specified.
function outputIsInVehicle ( sourcePlayer, commandName, checkedPlayerName )
    -- we get the player element from the nick specified
    local checkedPlayer = getPlayerFromNick ( checkedPlayerName )
    -- if it exists,
    if ( checkedPlayer ) then
        -- if it's in a vehicle,
        if isPlayerInVehicle ( checkedPlayer ) then
            -- tell the source player
            outputChatBox ( checkedPlayerName .. " is in a vehicle.", sourcePlayer )
        -- if it's not in a vehicle,
        else
            -- tell the source player
            outputChatBox ( checkedPlayerName .. " is not in a vehicle.", sourcePlayer )
        end
    -- if it doesn't exist,
    else
        -- tell the source player
        outputChatBox ( "Invalid player name.", sourcePlayer )
    end
end

-- define a handler for the isinvehicle command
addCommandHandler ( "isinvehicle", outputIsInVehicle )
```

See Also
--------
