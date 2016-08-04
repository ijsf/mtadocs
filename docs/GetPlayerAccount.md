This function returns the specified player's [account](/account.md "wikilink") object.

Syntax
------

``` lua
account getPlayerAccount ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") element you want to get the [account](/account.md "wikilink") of.

### Returns

Returns the player's account object, or *false* if the player passed to the function is invalid.

Example
-------

This example sets a player's money and also stores the value is his account.

``` lua
function setMoney(thePlayer,key,amount)
    local account = getPlayerAccount(thePlayer)
    if account and tonumber(amount) then
        setPlayerMoney (thePlayer,amount)
        setAccountData(account,"money",amount)
    end
end
addCommandHandler("setmoney",setMoney)
```

See Also
--------

[ar:getPlayerAccount](/ar:getPlayerAccount.md "wikilink") [ru:getPlayerAccount](/ru:getPlayerAccount.md "wikilink")
