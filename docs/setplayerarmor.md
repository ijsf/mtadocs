This function allows you to set the armor value of a [player](/docs/player.md "wikilink").

Syntax
------

``` lua
bool setPlayerArmor ( player thePlayer, float playerArmor )
```

### Required Arguments

-   **thePlayer**: the [player](/docs/player.md "wikilink") whose armor you want to modify.
-   **playerArmor**: the amount of armor you want to set on the player. Valid values are from 0 to 100.

### Returns

Returns *true* if the armor was changed succesfully. Returns *false* if an invalid player is specified, or the armor value specified is out of acceptable range.

Example
-------

<section name="Server" class="server" show="true">
This example removes the armor of a player.

``` lua
function givePlayerArmor ( player, command )
    setPlayerArmor ( player, 100 ) --Set player's armor to 100 when he types the command 'addarmor'
end
addCommandHandler ( "addarmor", givePlayerArmor )

function removePlayerArmor ( player, command )
    setPlayerArmor ( player, 0 ) --Set player's armor to 0 when he types the command 'removearmor'
end
addCommandHandler ( "removearmor", removePlayerArmor )
```

</section>
See Also
--------
