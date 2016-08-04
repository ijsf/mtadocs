This function will return the [serial](/docs/serial.md "wikilink") of the specified [ban](/ban.md "wikilink").

Syntax
------

``` lua
string getBanSerial ( ban theBan )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") you want to retrieve the serial of.

### Returns

Returns a *string* of the serial if everything was successful, *false* if invalid arguments are specified or if there was no serial specified for the [ban](/docs/ban.md "wikilink").

Example
-------

This example will show the user who banned a player the serial of that banned player.

``` lua
function banPlayerCommand ( thisPlayer, commandName, bannedName, reason )
    if ( hasObjectPermissionTo ( thisPlayer, "function.banPlayer" ) ) then -- If the command user has the rights
        local bannedPlayer = getPlayerFromName ( bannedName ) -- Get the ID from the player who gets banned
        if getElementType ( bannedPlayer ) == "player" then -- If it's a player
            local theBan = banPlayer ( bannedPlayer, thisPlayer, reason ) -- Ban the player
            outputChatBox ( "ban: " .. bannedName .. " successfully banned", thisPlayer ) -- Send the banner a succes message
            outputChatBox ( "At Serial: " ..getBanSerial ( theBan ), thisPlayer ) -- And send him the serial of the banned player
        end
    else
        outputChatBox ( "ban: You don't have enough permissions", thisPlayer ) -- If the command user doesn't have the permissions
    end
end
addCommandHandler ( "ban", banPlayerCommand )
```

See Also
--------

[ru:getBanSerial](/docs/ru:getbanserial.md "wikilink")
