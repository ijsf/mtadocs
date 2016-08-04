This function gets the owner of a [custom weapon](/docs/element/weapon.md "wikilink"). Weapon ownership system was, however, disabled, so this function always returns *false*. Please refer to [setWeaponOwner](/setWeaponOwner.md "wikilink") for details.

Syntax
------

``` lua
bool getWeaponOwner ( weapon theWeapon )
```

### Required Arguments

-   **theWeapon:** The weapon to get the owner of.

### Returns

This function was intended to return the [player](/docs/player.md "wikilink") which owns the [custom weapon](/Element/Weapon.md "wikilink"), and *false* if an error occured. However, at the moment it always returns *false*.

Example
-------

``` lua
function arma()
    minigun = createWeapon("minigun", 1, 1, 3)--Create the weapon
    setWeaponClipAmmo(minigun, 99999)
        setWeaponState(minigun, "firing")
    setWeaponProperty(minigun, "fire_rotation", 0, -30, 0)
    dueno = getWeaponOwner(minigun)--This gets the owner
    outputChatBox(tostring(dueno))--And this say it in the chatbox
end
addCommandHandler("weapon", arma)--CommandHandler
```

Requirements
------------

See also
--------
