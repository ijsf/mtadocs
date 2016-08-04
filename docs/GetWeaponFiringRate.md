This gets the firing rate to be used when a [custom weapon](/docs/Element/Weapon.md "wikilink") opens fire.

Syntax
------

``` lua
int getWeaponFiringRate ( weapon theWeapon )
```

### Required Arguments

-   **theWeapon:** The weapon to modify the firing rate of.

### Returns

Returns an *integer* with the firing rate of the custom weapon, *false* otherwise.

Example
-------

This example creates a minigun at the center of the map and creates a */firerate* command that outputs its firerate to the player who types it.

``` lua
local weapon = createWeapon("minigun", 0, 0, 3)

function outputMinigunFireRate()
    outputChatBox("Fire rate: " .. getWeaponFiringRate(weapon))
end
addCommandHandler("firerate", outputMinigunFireRate)
```

Requirements
------------

See also
--------
