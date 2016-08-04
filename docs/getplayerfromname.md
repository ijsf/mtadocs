This function returns a [player](/docs/player.md "wikilink") [element](/docs/element.md "wikilink") for the player with the name passed to the function.

Syntax
------

``` lua
player getPlayerFromName ( string playerName )
```

### Required Arguments

-   **playerName**: A string containing the name of the player you want to reference

### Returns

Returns a [player](/docs/player.md "wikilink") [element](/docs/element.md "wikilink") for the player with the nickname provided. If there is no player with that name, *false* is returned.

Example
-------

This example finds a [player](/docs/player.md "wikilink") as specified in the command and outputs the direction and distance he is from the player who entered the command. For example: 'locate someguy'.

``` lua
function locatePlayer( sourcePlayer, command, who )
    local targetPlayer = getPlayerFromName ( who )                -- find the player that was specified in the command
    if ( targetPlayer ) then                                      -- if a player was found
        local x,y,z = getElementPosition ( sourcePlayer )     -- save the position of the player who entered the command
        local xp,yp,zp = getElementPosition ( targetPlayer )  -- save the position of the player who should be located
        local dir = nil
        if (yp > y) then
            dir = "N"
        else
            dir = "S"
        end
        if (xp > x) then
            dir = dir .. "E"
        else
            dir = dir .. "W"
        end
        local distance = math.ceil ( getDistanceBetweenPoints3D(x, y, z, xp, yp, zp) )
        outputChatBox( who .. " found " .. dir .. " (" .. distance .. ")", sourcePlayer) -- output the message
    end
end
addCommandHandler ( "locate", locatePlayer )
```

See Also
--------

[ru:getPlayerFromName](/docs/ru-getplayerfromname.md "wikilink")
