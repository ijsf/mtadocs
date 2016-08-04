This function returns the client that is currently using a specified account, i.e. is logged into it. Only one client can use an account at a time.

Syntax
------

``` lua
client getAccountClient ( account theAccount )
```

### Required Arguments

-   **theAccount:** The account you wish to get the client of.

### Returns

Returns a [client](/docs/client.md "wikilink") element if the account is currently in use, *false* otherwise.

Example
-------

This example checks if the user attached to an account is a player, and if so if they're alive.

``` lua
function isAccountUserAlive ( theAccount )
    local theClient = getAccountClient ( theAccount )       -- get the client attached to the account
    if ( getElementType ( theClient ) == "player" ) then    -- see if it's a player (rather than an admin for example)
        if ( not isPlayerDead ( theClient ) ) then          -- if the player's health is greater than 0 
            return true
        end
    end
    return false
end
```

See Also
--------
