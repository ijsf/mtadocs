This function returns an integer that contains the ammo in a specified [ped](/docs/ped.md "wikilink")'s weapon. See [Weapon Info](/weapon.md "wikilink")

Syntax
------

``` lua
int getPedAmmoInClip ( ped thePed [, int weaponSlot = current ] )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") whose ammo you want to check.

### Optional Arguments

-   **weaponSlot:** an integer representing the weapon slot (set to the ped's currently selected slot if not specified).

### Returns

Returns an [int](/docs/int.md "wikilink") containing the amount of ammo in the specified ped's currently selected or specified clip, or 0 if the ped specified is invalid.

Example
-------

This example outputs the amount of ammo the specified player has in his current slot. For example: 'ammo someguy'.

``` lua
function showAmmo(thePlayer, command, who )
    local targetPlayer = getPlayerFromName ( who )
    if ( thePlayer ) then
        local ammo = getPedAmmoInClip ( targetPlayer )
        outputChatBox ( who .. " has " .. ammo .. " ammo in his active clip" )
    else
        outputChatBox ( "Player '" .. who .. "' not found." )
    end
end
addCommandHandler( "ammo", showAmmo )
```

Issues
------

See Also
--------
