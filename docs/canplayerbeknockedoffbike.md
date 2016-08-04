This function checks if a player can fall off bikes.

Syntax
------

``` lua
bool canPlayerBeKnockedOffBike ( player thePlayer )         
```

### Required Arguments

-   **thePlayer:** the player whose knockoffstatus being asked

### Returns

Returns *true* if the player can be knocked off bikes, *false* if he can't or an invalid element was passed.

Example
-------

This example puts the knockoff status in the chatbox.

``` lua
function canBeKnockedOff ( command )
    -- The player should enter /knockstatus
    if canPlayerBeKnockedOffBike ( getLocalPlayer() ) then
        outputChatBox ( "You can be knocked off your bike." )
    else
        outputChatBox ( "You can't be knocked off your bike." )
    end
end
addCommandHandler ( "knockstatus", canBeKnockedOff )
```

See Also
--------
