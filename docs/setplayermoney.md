Sets a player's money to a certain value, regardless of current player money. It should be noted that setting negative values does not work and in fact gives the player large amounts of money.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setPlayerMoney ( player thePlayer, int amount [, bool instant = false ] ) 
```

### Required Arguments

-   **thePlayer:** Which player to set the money of.
-   **amount:** A whole integer specifying the new amount of money the player will have.

### Optional Arguments

</section>
<section name="Client" class="client" show="true">
``` lua
bool setPlayerMoney ( int amount [, bool instant = false ] ) 
```

### Required Arguments

-   **amount:** A whole integer specifying the new amount of money the local player will have.

### Optional Arguments

</section>
### Returns

Returns *true* if the money was added, or *false* if invalid parameters were passed.

Example
-------

**Example 1:** This example sets the player's money to the desired amount when he types “setcash” in console.

``` lua
function setCash(thePlayer, command, amount)       -- when the setcash function is called
    setPlayerMoney(thePlayer, tonumber(amount))    -- change player's money to the desired amount
end
addCommandHandler("setcash", setCash)           -- add a command handler for setcash
```

**Example 2:** This sets all players the amount of 1337 money when “leet” is typed in console.

``` lua
function leetmoney()
    setPlayerMoney(root, 1337)
end
addCommandHandler("leet", leetmoney)
```

See Also
--------

[ru:setPlayerMoney](/docs/ru-setplayermoney.md "wikilink")
