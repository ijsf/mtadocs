This function retrieves the name of an [account](/docs/account.md "wikilink").

Syntax
------

``` lua
string getAccountName ( account theAccount )
```

### Required Arguments

-   **theAccount:** The account you wish to get the name of.

### Returns

Returns a string containing the account's name, *false* if the account does not exist or an invalid argument was passed to the function.

Example
-------

This example announces into the console when a player logs into his account.

``` lua
function outputOnLogin ( previous_account, current_account, auto_login ) --when a player logs in
    outputConsole(getAccountName(previous_account).." Logged into "..getAccountName(current_account)) -- announce it into the console
end
addEventHandler("onPlayerLogin",getRootElement(),outputOnLogin ) --add an event handler
```

See Also
--------

[ru:getAccountName](/docs/ru-getaccountname.md "wikilink") [es:getAccountName](/docs/es-getaccountname.md "wikilink") [ar:getAccountName](/docs/ar-getaccountname.md "wikilink") [pl:GetAccountName](/docs/pl-getaccountname.md "wikilink")
