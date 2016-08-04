Returns the amount of money a player currently has.

**Note:** The amount may vary between the server and client, you shouldn't trust the client side value to always be accurate.

Syntax
------

<section show="true" name="Server" class="server">
``` lua
int/bool getPlayerMoney ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player you wish the retrieve the amount of money from.

### Returns

Returns an integer with the amount of money the specified player has, *false* if the player is invalid.

</section>
<section show="true" name="Client" class="client">
``` lua
int getPlayerMoney ( )
```

### Returns

Returns an integer with the amount of money the local player has.

</section>
Example
-------

<section show="true" name="Server" class="server">
When a player types '/checkMoney' this example retrieves the player's money and outputs a message according to the value.

``` lua
function checkMoney(thePlayer, command)
    local money = getPlayerMoney(thePlayer)                                -- get the amount of money from the player who entered the command
    if (money > 1000) then                                                 -- if money is more than 1000
        outputChatBox("You are rich: " .. tostring(money), thePlayer)  -- output this message together with the money
    else
        outputChatBox("Poor guy...", thePlayer)                        -- and else, output this message
    end
end
addCommandHandler("checkMoney", checkMoney)                                    -- add the console command
```

</section>
See Also
--------

[ru:getPlayerMoney](/docs/ru-getplayermoney.md "wikilink")
