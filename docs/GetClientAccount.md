This function returns the specified client's [account](/docs/account.md "wikilink") object.

Syntax
------

``` lua
account getClientAccount ( client theClient )
```

### Required Arguments

-   **theClient:** The client [element](/docs/element.md "wikilink") (player or admin) you want to get the account of.

### Returns

Returns the client's account object, or *false* if the client passed to the function is invalid.

Example
-------

This example sets a player's money and also stores the value is his account.

``` lua
function setMoney ( thePlayer, key, amount )
    setPlayerMoney ( thePlayer, amount )
    account = getClientAccount ( thePlayer )
    if ( account ) then
        setAccountData ( account, "money", amount )
    end
end
addCommandHandler ( "setmoney", setMoney )
```

See Also
--------
