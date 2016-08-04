This function sets a [custom weapon](/Element/Weapon.md "wikilink")'s state.

Syntax
------

``` lua
bool setWeaponState ( weapon theWeapon, string theState )
```

### Required Arguments

-   **theWeapon**: the weapon you wish to set the state of.
-   **theState**: the state you wish to set:
    -   **reloading**: makes the weapon reload.
    -   **firing**: makes the weapon constantly fire its target (unless any shooting blocking flags are set) according to its assigned firing rate.
    -   **ready**: makes the weapon stop reloading or firing.

### Returns

Returns *true* on success, *false* otherwise.

### Example

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
      function()
            local wep = createWeapon("m4", 0, 0, 4)
            setWeaponState(wep, "firing")
      end
)
```

Requirements
------------

See also
--------
