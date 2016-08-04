This function adds money to a [player](/docs/player.md "wikilink")'s current money amount. To set absolute values, [setPlayerMoney](/setPlayerMoney.md "wikilink") can be used.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool givePlayerMoney ( player thePlayer, int amount )
```

### Required Arguments

-   **thePlayer:** the [player](/docs/player.md "wikilink") you are giving the money to.
-   **amount:** a positive integer number specifying the amount of money to give to the player.

</section>
<section name="Client" class="client" show="true">
``` lua
bool givePlayerMoney ( int amount )
```

### Required Arguments

-   **amount:** a positive integer number specifying the amount of money to give to the player.

</section>
### Returns

Returns *true* if the money was added, or *false* if invalid parameters were passed.

Example
-------

<section show="true" name="Example 1 - Client and Server" class="server">
This example gives a player money when using “givecash” command.

``` lua
function consoleGiveCash ( thePlayer, command, amount ) --when the givecash command is called
    givePlayerMoney ( thePlayer, amount ) --give the player money according to the amount
end
addCommandHandler ( "givecash", consoleGiveCash  ) --add a handler function for the command "givecash"
```

</section>
<section show="true" name="Example 2 - Server" class="server">
This example gives a player one thousand dollars, as a reward for killing another player.

``` lua
function rewardOnWasted ( ammo, killer, killerweapon, bodypart )
    --if there is a killer, and that killer is not the same person as whoever died
    if ( killer ) and ( killer ~= source ) then 
        givePlayerMoney ( killer, 1000 ) --reward the killer with 1000 cash.
    end
end
addEventHandler ( "onPlayerWasted", getRootElement(), rewardOnWasted ) --attach the rewardOnWasted function to the relevant event.
```

</section>
<section show="true" name="Example 3 - Server" class="server">
This example Creates money Money (dollar symbol) pickup and gives 30,000 dollars on Pick up hit.

``` lua
local money = createPickup (1896.4000244141, -1950.9000244141, 13, 3, 1274, 10000 )
function pickupUse ( player )
    givePlayerMoney ( player, 30000 )
end
addEventHandler ( "onPickupUse", money, pickupUse )
```

</section>
See Also
--------

[ru:GivePlayerMoney](/docs/ru:GivePlayerMoney.md "wikilink")
