This function returns an [account](/account.md "wikilink") for a specific user.

Syntax
------

``` lua
account getAccount ( string username, [ string password ] )
```

### Required Arguments

-   **username:** The username of the account you want to retrieve

### Optional Arguments

-   **password:** The password for the account. If this argument is not specified, you can get the account whatever password it is, otherwise the password must match the account's.

### Returns

Returns an [account](/account.md "wikilink") or *false* if an account matching the username specified (and password, if specified) could not be found.

Example
-------

``` lua
addEventHandler("onPlayerJoin",root,function()
    if getAccount(getPlayerName(source)) then
        outputChatBox("Please Login!",source)
    else
        outputChatBox("Please Register!",source)
    end
end)
```

See Also
--------

[ar:getAccount](/ar:getAccount.md "wikilink") [es:getAccount](/es:getAccount.md "wikilink") [pl:GetAccount](/pl:GetAccount.md "wikilink") [ru:getAccount](/ru:getAccount.md "wikilink")
