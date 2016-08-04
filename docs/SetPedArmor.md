This function allows you to set the armor value of a [ped](/ped.md "wikilink").

Syntax
------

``` lua
bool setPedArmor ( ped thePed, float armor )
```

### Required Arguments

-   **thePed**: the [ped](/ped.md "wikilink") whose armor you want to modify.
-   **armor**: the amount of armor you want to set on the ped. Valid values are from 0 to 100.

### Returns

Returns *true* if the armor was changed succesfully. Returns *false* if an invalid ped was specified, or the armor value specified is out of acceptable range.

Example
-------

This example removes the armor of a player.

``` lua
function givePlayerArmor ( player, command )
    setPedArmor ( player, 100 )    -- Set player's armor to 100 when he types the command 'addarmor'
end
addCommandHandler ( "addarmor", givePlayerArmor )

function removePlayerArmor ( player, command )
    setPedArmor ( player, 0 )      -- Set player's armor to 0 when he types the command 'removearmor'
end
addCommandHandler ( "removearmor", removePlayerArmor )
```

In this, adds an amount of armor that the player defined in command 'addarmor'.

``` lua
function givePlayerArmor( player, command, amount )
    if getPedArmor(player) == 100 then
        return
        outputChatBox("Your armor already is complete!", player, 220, 0, 0 ) -- Inform the player if your armor already is complete.
    end
    if amount and tonumber(amount) >= 1 or tonumber(amount) <= 100 then -- If amount is between 1 and 100.
        setPedArmor( player, tonumber(amount) )    -- Set amount armor that player chosen on the command.
    else
        return
    end
    if not amount then
        outputChatBox( "sintax: /addarmor [armor-amount]", player, 220, 0, 0 ) -- Inform the player if 'amount' argument is missing.
    end
end
addCommandHandler( "addarmor", givePlayerArmor )
```

See Also
--------

[ru:setPedArmor](/ru:setPedArmor.md "wikilink")
