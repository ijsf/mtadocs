Syntax
------

### Required Arguments

-   **bannedPlayer:** The player that will be banned from the server.

### Optional Arguments

-   **responsibleElement:** The element that is responsible for banning the player. This can be a player or the root ([getRootElement](/getRootElement.md "wikilink")()) (Maximum 30 characters if using a string).
-   **reason:** The reason the player will be banned from the server.
-   **seconds:** The amount of seconds the player will be banned from the server for. This can be 0 for an infinite amount of time.

### Returns

Returns a [ban](/ban.md "wikilink") object if banned successfully, or *false* if unsuccessful.

Example
-------

This example lets a player ban anyone if he has ACL rights.

``` lua
--Add the "ban" command handler
-- Example with the player
function banPlayerCommand ( theClient, commandName, bannedName, reason )

    -- Give the player a nice error if he doesn't have rights
    if ( hasObjectPermissionTo ( theClient, "function.banPlayer" ) ) then
        --Get player element from the name
        local bannedPlayer = getPlayerFromName ( bannedName )

        --Ban the player
        banPlayer ( bannedPlayer, theClient, reason )
        outputChatBox ( "ban: " .. bannedName .. " successfully banned", theClient )

    else
        outputChatBox ( "ban: You don't have enough permissions", theClient )
    end

end
addCommandHandler ( "ban", banPlayerCommand )

-- Example function with the root element. Here you would pass a player element to the function.
function banCheater(theCheater)
    banPlayer(theCheater, getRootElement(), "You are banned because of cheating.")
end
```

This example is Firewall Account Player by serial on Login

``` lua
Firewall = 
{
    [ 'AccountName' ] = 'SerialPlayer',
    [ '3ash8' ] = '9C9F3B55D9D7BB7135FF274D3BF444E4',
    [ 'test5' ] = '1D6F76CF8D7193792D13789849498452',
}
 
addEventHandler ( 'onPlayerLogin', getRootElement ( ),
    function ( _, theCurrentAccount )
    local Serial = Firewall[getAccountName(theCurrentAccount)]
        if ( Serial ) then
            if Serial ~= getPlayerSerial ( source ) then
                banPlayer ( source, false, false, true, getRootElement ( ), 'reason ban' )
            end
        end
    end
)
```

See Also
--------

[es:banPlayer](/es:banPlayer.md "wikilink") [ru:BanPlayer](/ru:BanPlayer.md "wikilink")
