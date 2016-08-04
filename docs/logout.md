This function logs the given player out of his current [account](/docs/account.md "wikilink").

Syntax
------

``` lua
bool logOut ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player to log out of his current account

### Returns

Returns *true* if the player was successfully logged out, *false* or *nil* if it failed for some reason, ie. the player was never logged in.

Example
-------

This example logs every player out of their account when the resource is (re)started. This would be handy for resources that show a login screen onClientResourceStart.

``` lua
function logoutAll ()
    local players = getElementsByType ( "player" ) -- Get every player
        for k, player in ipairs ( players ) do -- For every player do the following...
            account = getPlayerAccount ( player ) -- Get every player's account
                if ( not isGuestAccount ( account ) ) then -- For every player that's logged in....
                    logOut ( player ) -- Log them out.
                end
        end
end
 -- Trigger it when the resource (re)starts
addEventHandler ( "onResourceStart", getResourceRootElement(), logoutAll )
```

See Also
--------

[ar:setAccountPassword](/docs/ar:setaccountpassword.md "wikilink")
