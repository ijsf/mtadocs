This function returns a table over all the [accounts](/docs/account.md "wikilink") that exist in the server internal.db file. (Note: accounts.xml is no longer used after version 1.0.4)

Syntax
------

``` lua
table getAccounts ()
```

### Returns

A [table](/docs/table.md "wikilink") over the accounts that exist in the server internal.db file. This table might be empty.

Example
-------

``` lua
function printAmountOfAccounts ( thePlayer )
    local accountTable = getAccounts () -- return the table over accounts
    if #accountTable == 0 then -- if the table is empty
        outputChatBox( "There are no accounts. :(", thePlayer )
    else -- table isn't empty
        outputChatBox( "There are " .. #accountTable .. " accounts in this server!", thePlayer )
    end
end
addCommandHandler( "accountcount", printAmountOfAccounts ) -- add a command handler for command 'accountcount'
```

See Also
--------

[ru:getAccounts](/docs/ru:getAccounts.md "wikilink")
