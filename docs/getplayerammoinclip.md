This function returns an integer that contains the ammo in a specified [player](/docs/player.md "wikilink")'s weapon. See [Weapon Info](/docs/weapon.md "wikilink")

Syntax
------

<section name="Server" class="server" show="true">
``` lua
int getPlayerAmmoInClip ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose ammo you want to check.

### Returns

Returns an [int](/docs/int.md "wikilink") containing the amount of ammo in the player's currently selected clip, or 0 if the player specified is invalid.

</section>
<section name="Client" class="client" show="true">
``` lua
int getPlayerAmmoInClip ( player thePlayer, int weaponSlot )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose ammo you want to check.
-   **weaponSlot:** an integer representing the weapon slot.

### Returns

Returns an [int](/docs/int.md "wikilink") containing the amount of ammo in the specified player's currently selected or specified clip, or 0 if the player specified is invalid.

</section>
Example
-------

<section name="Server" class="server" show="true">
This example outputs the amount of ammo the specified player has in his current slot. For example: 'ammo someguy'.

``` lua
function showAmmo( thePlayer, command, who )
    local targetPlayer = getPlayerFromNick ( who )
    if ( thePlayer ) then
        local ammo = getPlayerAmmoInClip ( targetPlayer )
        outputChatBox ( who .. " has " .. ammo .. " ammo in his active clip", thePlayer )
    else
        outputChatBox ( "Player '" .. who .. "' not found.", thePlayer )
    end
end
addCommandHandler( "ammo", showAmmo )
```

</section>
See Also
--------
