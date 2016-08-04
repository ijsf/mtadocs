This function returns the [player](/docs/player.md "wikilink") element that is currently using a specified [account](/docs/account.md "wikilink"), i.e. is logged into it. Only one player can use an account at a time.

Syntax
------

``` lua
player getAccountPlayer ( account theAccount )
```

### Required Arguments

-   **theAccount:** The [account](/docs/account.md "wikilink") you wish to get the [player](/docs/player.md "wikilink") of.

### Returns

Returns a [player](/docs/player.md "wikilink") element if the account is currently in use, *false* otherwise.

Example
-------

This example checks if the user attached to an account is a player, and if so if they're alive.

``` lua
function isAccountUserAlive ( theAccount )
    local thePlayer = getAccountPlayer ( theAccount )       -- get the client attached to the account
    if ( getElementType ( thePlayer ) == "player" ) then    -- see if it really is a player (rather than a console admin for example)
        return not isPedDead(thePlayer)             -- if the player's health is greater than 0 
    end
    return false
end
```

See Also
--------

[ru:getAccountPlayer](/docs/ru-getaccountplayer.md "wikilink") [ar:getAccountPlayer](/docs/ar-getaccountplayer.md "wikilink") [pl:GetAccountPlayer](/docs/pl-getaccountplayer.md "wikilink")
