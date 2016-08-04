This function sets the ammo left in a [custom weapon](/docs/element/weapon.md "wikilink")'s magazine/clip.

Syntax
------

``` lua
bool setWeaponClipAmmo ( weapon theWeapon, int clipAmmo )
```

### Required Arguments

-   **theWeapon:** The [weapon](/docs/element/weapon.md "wikilink") to set the clip ammo of.
-   **clipAmmo:** The amount of ammo in the clip.

### Returns

This function returns *true* if the arguments are valid and the weapon clip ammo could be changed; *false* otherwise.

Example
-------

This example adds a */weapon* command that creates a M4 where the player uses it, and gives 1 clip ammo to it.

``` lua
function createWeaponWithLowClipAmmo()
    local wep = createWeapon("m4", getElementPosition(localPlayer))
    setWeaponClipAmmo(wep, 1) -- Give the weapon 1 clip ammo, so it will reload at the next shoot.
end
addCommandHandler("weapon", createWeaponWithLowClipAmmo)
```

Requirements
------------

See also
--------
