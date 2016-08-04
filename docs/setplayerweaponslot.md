Please use [setPedWeaponSlot](/docs/setpedweaponslot.md "wikilink")

This function sets the player's weapon slot. This affects the current weapon.

Syntax
------

``` lua
bool setPlayerWeaponSlot ( player theplayer, int weapon_slot )
```

### Required Arguments

-   **theplayer:** the [player](/docs/player.md "wikilink") whose weapon slot you want to set. In a clientside script, this can only be the local player.
-   **weapon\_slot:** the weapon slot to set.

### Returns

Returns *true* if successful in setting the player's equipped weapon slot, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example allows the player to type the command 'giveweapons', which gives the player a weapon for every slot. Instead of equipping the last given weapon, the script randomly decides which weapon to equip after all the weapons are given.

``` lua
function givePlayerWeapons ( player, commandName )
        --Give the player a weapon for each slot
    giveWeapon ( player, 1, 1 )
    giveWeapon ( player, 2, 1 )
    giveWeapon ( player, 22, 1 )
    giveWeapon ( player, 25, 1 )
    giveWeapon ( player, 28, 1 )
    giveWeapon ( player, 30, 1 )
    giveWeapon ( player, 33, 1 )
    giveWeapon ( player, 35, 1 )
    giveWeapon ( player, 16, 1 )
    giveWeapon ( player, 42, 1 )
    giveWeapon ( player, 10, 1 )
    giveWeapon ( player, 44, 1 )
    giveWeapon ( player, 40, 1 )
        --Randomly select which weapon to equip, slots 1 through 12
    setPlayerWeaponSlot ( player, math.random ( 1, 12) )
end
addCommandHandler ( "giveweapons", givePlayerWeapons )
```

</section>
See Also
--------
