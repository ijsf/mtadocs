This function retrieves a string that has been stored using [setAccountData](/setAccountData.md "wikilink"). Data stored as account data is persistent across user's sessions and maps, unless they are logged into a guest account.

Syntax
------

``` lua
string getAccountData ( account theAccount, string key )
```

### Required Arguments

-   **theAccount:** The account you wish to retrieve the data from.
-   **key:** The key under which the data is stored

### Returns

Returns a [string](/string.md "wikilink") containing the stored data or *false* if no data was stored under that key.

Example
-------

For a pirate roleplaying gametype, the amount of money a player has is made persistent by storing it in his account. Note the code uses “piraterpg.money” as key instead of just “money”, as the player may be participating in other gametypes that also save his money amount to his account. If both gametypes would use “money” as the account key, they'd overwrite each other's data.

``` lua
function onPlayerQuit()
      local playerAccount = getPlayerAccount(source) -- get his account
      if (playerAccount) then -- if we got the account then
            local playerMoney = getPlayerMoney(source) -- get his money amount
            setAccountData(playerAccount, "piraterpg.money", playerMoney) -- store his current money amount in his account data
      end
end
addEventHandler("onPlayerQuit", getRootElement(), onPlayerQuit) -- add an event handler

function onPlayerLogin(_,account)
    local playerMoney = getAccountData(account, "piraterpg.money") -- get the money amount was store in his account data
    -- make sure there was actually a value saved under this key (check if playerMoney is not false).
    -- this will for example not be the case when a player plays the gametype for the first time
    if (playerMoney) then
        setPlayerMoney(source, playerMoney)
    end
end
addEventHandler("onPlayerLogin", getRootElement(), onPlayerLogin) -- add an event handler
```

See Also
--------

[ru:getAccountData](/ru:getAccountData.md "wikilink") [ar:getAccountData](/ar:getAccountData.md "wikilink") [pl:getAccountData](/pl:getAccountData.md "wikilink")
