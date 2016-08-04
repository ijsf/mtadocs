This function resets the firing rate of a [custom weapon](/Element/Weapon.md "wikilink") to the default one.

Syntax
------

``` lua
bool resetWeaponFiringRate ( weapon theWeapon )
```

### Required Arguments

-   **theWeapon:** the weapon to reset the firing rate of.

### Returns

Returns *true* on success, *false* otherwise.

### Example

``` lua
local weapon = createWeapon ("mp5",0,0,10) 
resetWeaponFiringRate (weapon)
```

Requirements
------------

See also
--------
