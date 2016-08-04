This function sets a string to be stored in an [account](/docs/account.md "wikilink"). This can then be retrieved using [getAccountData](/docs/getaccountdata.md "wikilink"). Data stored as account data is persistent across user's sessions and maps, unless they are logged into a guest account. Even if logged into a guest account, account data can be useful as a way to store a reference to your own account system, though it's persistence is equivalent to that of using [setElementData](/docs/setelementdata.md "wikilink") on the player's element.

Syntax
------

``` lua
bool setAccountData ( account theAccount, string key, string value )
```

### Required Arguments

-   **theAccount:** The account you wish to retrieve the data from.
-   **key:** The key under which you wish to store the data
-   **value:** The value you wish to store. Set to false to remove the data. **NOTE:** you cannot store tables as values, but you can use [toJSON](/docs/tojson.md "wikilink") strings.

### Returns

Returns a *true* if the account data was set, *false* if an invalid argument was specified.

Example
-------

For a pirate roleplaying gametype, the amount of money a player has is made persistent by storing it in his account. Note the code uses “piraterpg.money” as key instead of just “money”, as the player may be participating in other gametypes that also save his money amount to his account. If both gametypes would use “money” as the account key, they'd overwrite each other's data.

``` lua
function onPlayerQuit ( )
      -- when a player leaves, store his current money amount in his account data
      local playeraccount = getPlayerAccount ( source )
      if ( playeraccount ) and not isGuestAccount ( playeraccount ) then -- if the player is logged in
            local playermoney = getPlayerMoney ( source ) -- get the player money
            setAccountData ( playeraccount, "piraterpg.money", playermoney ) -- save it in his account
      end
end
 
function onPlayerLogin (_, playeraccount )
      -- when a player logins, retrieve his money amount from his account data and set it
      if ( playeraccount ) then
            local playermoney = getAccountData ( playeraccount, "piraterpg.money" )
            -- make sure there was actually a value saved under this key (check if playermoney is not false).
            -- this will for example not be the case when a player plays the gametype for the first time
            if ( playermoney ) then
                  setPlayerMoney ( source, playermoney )
            end
      end
end
 
addEventHandler ( "onPlayerQuit", getRootElement ( ), onPlayerQuit )
addEventHandler ( "onPlayerLogin", getRootElement ( ), onPlayerLogin )
```

Issues
------

### Workaround for issue 7757

Convert your floating point number to a string.

``` lua
setAccountData(account, "myKey", tostring(0.123))
```

See Also
--------

[ar:setAccountData](/docs/ar-setaccountdata.md "wikilink") [es:setAccountData](/docs/es-setaccountdata.md "wikilink")
