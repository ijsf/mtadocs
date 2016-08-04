Checks whether or not a ped is currently in water.

Syntax
------

``` lua
bool isPedInWater ( ped thePed )
```

### Required Arguments

-   **thePed:** the ped you want to check

### Returns

Returns *true* if the ped is in water, *false* if he is not or an invalid element was passed.

Example
-------

<section name="Client" class="client" show="true">
This example shows all players that are in water in a list to the player who enters the 'playersInWater' command.

``` lua
function showPlayersInWater ( sourcePlayer, command )
    local players = getElementsByType ( "player" )
    local list = ""
    for k,v in ipairs ( players ) do
        if isPedInWater ( v ) then
            list = list .. " " .. getPlayerName ( v )
        end
    end
    outputChatBox("Players pretending to be trouts: " .. list, sourcePlayer)
end
addCommandHandler("playersInWater", showPlayersInWater)
```

</section>
See Also
--------
