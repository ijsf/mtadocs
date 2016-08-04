This function will kick the specified player from the server.

Syntax
------

``` lua
bool kickPlayer ( player kickedPlayer, [ player responsiblePlayer, string reason = "" ] )         
```

*or*

``` lua
bool kickPlayer ( player kickedPlayer, [ string reason = "" ] )
```

### Required Arguments

-   **kickedPlayer:** The player that will be kicked from the server

### Optional Arguments

-   **responsiblePlayer:** The player that is responsible for the event. **Note**: If left out as in the second syntax, responsible player for the kick will be “Console” (Maximum 30 characters if using a string).
-   **reason:** The reason for the kick. (Maximum 64 characters)

### Returns

Returns *true* if the player was kicked succesfully, *false* if invalid arguments are specified.

Example
-------

This example lets a player kick anyone who has a lower level.

``` lua
function kickPlayerHandler ( sourcePlayer, commandname, kickedname, reason )
    -- Get player element from the name
    local kicked = getPlayerFromName ( kickedname )
    -- If the client who sent the command has a higher level
    if ( hasObjectPermissionTo ( sourcePlayer, "function.kickPlayer" ) ) then
        -- Kick the player
        kickPlayer ( kicked, sourcePlayer, reason )
    end
end
-- Add the "kick" command handler
addCommandHandler ( "kick", kickPlayerHandler )
```

See Also
--------

[es:kickPlayer](/docs/es-kickplayer.md "wikilink") [ru:kickPlayer](/docs/ru-kickplayer.md "wikilink")
