This function sets the firing rate to be used when a [custom weapon](/docs/element/weapon.md "wikilink") is in *firing* state.

Syntax
------

``` lua
bool setWeaponFiringRate ( weapon theWeapon, int firingRate )
```

### Required Arguments

-   **theWeapon:** The weapon to modify the firing rate of.
-   **firingRate:** The weapon firing rate. It seems to be a kind of frecuency value, so the lower the quicker the [custom weapon](/docs/element/weapon.md "wikilink") will shoot.

### Returns

Returns *true* on success, *false* otherwise.

Example
-------

This example makes the Desert Eagle gun fire faster.

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
function()
   local weapon = createWeapon ("deagle",0,0,10) -- create the weapon (deagle)
   setWeaponAmmo(weapon,5000) -- set weapon ammo to 5000
   setWeaponState(weapon, "firing") -- in firing state.
   setWeaponFiringRate (weapon,2) -- change the weapon firing rate
end
)
```

Requirements
------------

See also
--------
