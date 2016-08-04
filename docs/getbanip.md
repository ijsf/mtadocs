This function will return the IP of the specified [ban](/docs/ban.md "wikilink").

Syntax
------

``` lua
string getBanIP ( ban theBan )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") in which you want to return the IP of.

### Returns

Returns a *string* of the IP if everything was successful, *false* if invalid arguments are specified if there was no IP specified for the [ban](/docs/ban.md "wikilink").

Example
-------

This example will show the user who banned a player the IP adress of that banned player.

``` lua
function banPlayerCommand ( thisPlayer, commandName, bannedName, reason )
    if ( hasObjectPermissionTo ( thisPlayer, "function.banPlayer" ) ) then -- If the command user has the rights
        local bannedPlayer = getPlayerFromNick ( bannedName ) -- Get the ID from the player who gets banned
        if getElementType ( bannedPlayer ) == "player" then -- If it's a player
            local theBan = banPlayer ( bannedPlayer, thisPlayer, reason ) -- Ban the player
            outputChatBox ( "ban: " .. bannedName .. " successfully banned", thisPlayer ) -- Send the banner a succes message
            outputChatBox ( "At IP Adress: " ..getBanIP ( theBan ), thisPlayer ) -- And send him the IP adress of the banned player
        end
    else
        outputChatBox ( "ban: You don't have enough permissions", thisPlayer ) -- If the command user doesn't have the permissions
    end
end
addCommandHandler ( "ban", banPlayerCommand )
```

See Also
--------

[ru:getBanIP](/docs/ru:getBanIP.md "wikilink")
