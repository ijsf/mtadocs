This function changes the selected weapon slot of a [ped](/docs/ped.md "wikilink").

Syntax
------

``` lua
bool setPedWeaponSlot ( ped thePed, int weaponSlot )
```

### Required Arguments

-   **thePed:** the [ped](/docs/ped.md "wikilink") whose weapon slot you want to set. In a clientside script, this cannot be used on remote players.
-   **weaponSlot:** the weapon slot to set.

### Returns

Returns *true* if successful in setting the ped's equipped weapon slot, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example allows the player to type the command 'giveweapons', which gives the player a weapon for every slot. Instead of equipping the last given weapon, the script randomly decides which weapon to equip after all the weapons are given.

``` lua
function givePlayerWeapons ( thePlayer, commandName )
        -- Give the player a weapon for each slot
    giveWeapon ( thePlayer, 1, 1 )
    giveWeapon ( thePlayer, 2, 1 )
    giveWeapon ( thePlayer, 22, 1 )
    giveWeapon ( thePlayer, 25, 1 )
    giveWeapon ( thePlayer, 28, 1 )
    giveWeapon ( thePlayer, 30, 1 )
    giveWeapon ( thePlayer, 33, 1 )
    giveWeapon ( thePlayer, 35, 1 )
    giveWeapon ( thePlayer, 16, 1 )
    giveWeapon ( thePlayer, 42, 1 )
    giveWeapon ( thePlayer, 10, 1 )
    giveWeapon ( thePlayer, 44, 1 )
    giveWeapon ( thePlayer, 40, 1 )
        -- Randomly select which weapon to equip, slots 1 through 12
    setPedWeaponSlot ( thePlayer, math.random ( 1, 12) )
end
addCommandHandler ( "giveweapons", givePlayerWeapons )
```

</section>
See Also
--------

[ru:setPedWeaponSlot](/docs/ru-setpedweaponslot.md "wikilink")
