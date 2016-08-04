This function is used to delete existing player [accounts](/docs/account.md "wikilink").

Syntax
------

``` lua
bool removeAccount ( account theAccount )
```

### Required Arguments

-   **theAccount:** The account you wish to remove

### Returns

Returns *true* if account was successfully removed, *false* if the account does not exist.

Example
-------

This example does...

``` lua
function onCmdDeregister ( playerSource, commandName )
    -- grab the account
    local sourceAccount = getPlayerAccount ( playerSource )
    if sourceAccount then
        removeAccount ( sourceAccount )
        outputChatBox ( "Account deregistered for " .. getPlayerName ( playerSource ) )
    else 
        outputChatBox ( "Unable to get your account, make sure you are logged in", playerSource )
    end
end
 
addCommandHandler("deregister",onCmdDeregister)
```

See Also
--------

[ar:setAccountPassword](/docs/ar-setaccountpassword.md "wikilink")
