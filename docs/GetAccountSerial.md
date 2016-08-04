Syntax
------

``` lua
string getAccountSerial ( account theAccount )
```

### Required Arguments

-   **theAccount:** The [account](/docs/account.md "wikilink") to get serial from

### Returns

Returns *string* containing the serial, the string is empty if the account was never used. Returns *false* if invalid arguments were specified.

Example
-------

This example adds command *getaccserial* that outputs the given account's serial in the chat box.

``` lua
addCommandHandler("getaccserial", 
    function (player, cmd, accountName)
        local account = getAccount(accountName)
        if (account) then
            outputChatBox("Serial: " .. getAccountSerial(account))
        else
            outputChatBox("Account not found")
        end
    end)
```

See Also
--------
