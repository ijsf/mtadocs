Syntax
------

``` lua
table getAccountsBySerial ( string serial )
```

### Required Arguments

-   **serial:** The [serial](/docs/serial.md "wikilink") to get accounts from

### Returns

Returns *[table](/docs/table.md "wikilink")* containing the accounts associated with specified serial. Returns *false* if invalid arguments were specified.

Example
-------

This example adds command *getAccounts* that outputs the number of accounts a player has in the chat box.

``` lua
addCommandHandler("getAccounts", 
    function (player, cmd)
        local serial = getPlayerSerial(player)
        local accounts = getAccountsBySerial(serial)
        outputChatBox("You have " .. #accounts .. " accounts.", player)
    end)
```

See Also
--------

[pl:getAccountsBySerial](/docs/pl:getaccountsbyserial.md "wikilink")
