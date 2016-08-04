This function allows you to identify the weapon slot that a weapon belongs to.

Syntax
------

``` lua
int getSlotFromWeapon ( int weaponid )
```

### Required Arguments

-   **weaponid:** [Weapon](/docs/Weapon.md "wikilink") to find the weapon slot of.

### Returns

Returns an integer representing the given weapon ID's associated weapon slot, *false* if the ID was invalid.

Example
-------

This will output to the chatbox what weapon slot a given weapon number belongs to when entered into the console (i.e. 'getWeaponSlot 10').

``` lua
function outputWeaponSlot ( source, commandName, weaponID )
    local weaponSlot = getSlotFromWeapon ( weaponID )
    
    if (weaponSlot) then
        outputChatBox ( "Weapon ID " .. weaponID ..  " is in weapon slot " .. weaponSlot)
    else
        outputChatBox ( "Invalid weapon ID" )
    end
end
addCommandHandler ( "getWeaponSlot", outputWeaponSlot )
```

See Also
--------

[Weapon IDs](/docs/Weapons.md "wikilink") [ru:getSlotFromWeapon](/ru:getSlotFromWeapon.md "wikilink")
