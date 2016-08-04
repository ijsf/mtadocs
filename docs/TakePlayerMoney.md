This function subtracts money from a [player](/player.md "wikilink")'s current money amount.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool takePlayerMoney ( player thePlayer, int amount )
```

#### Required Arguments

-   **thePlayer:** the [player](/player.md "wikilink") you are taking the money from.
-   **amount:** an integer number specifying the amount of money to take from the player.

</section>
<section name="Client" class="client" show="true">
``` lua
bool takePlayerMoney ( int amount )
```

#### Required Arguments

-   **amount:** an integer number specifying the amount of money to take from the player.

</section>
### Returns

Returns *true* if the money was taken, or *false* if invalid parameters were passed.

Example
-------

<section name="Server" class="server" show="true">
This example takes money from a player when he types “takecash *number*” in the console.

``` lua
function takeCash ( thePlayer, command, amount )     -- when the takecash command is called
     takePlayerMoney ( thePlayer, tonumber(amount) ) -- take the amount of money from the player
end
addCommandHandler ( "takecash", takeCash )           -- add a handler function for the command "takecash"
```

</section>
See Also
--------

[ru:takePlayerMoney](/ru:takePlayerMoney.md "wikilink")
