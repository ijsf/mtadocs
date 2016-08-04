Creates a [custom weapon](/docs/element/weapon.md "wikilink") that can fire bullets. **Do not confuse this with player held weapons**.

Syntax
------

``` lua
weapon createWeapon ( string theType, float x, float y, float z )
```

### Required Arguments

-   **theType:** The weapon type which can be:

-   **x:** The x position to create the weapon.
-   **y:** The y position to create the weapon.
-   **z:** The z position to create the weapon.

### Returns

Returns a [custom weapon](/docs/element/weapon.md "wikilink") element, which represents a weapon floating at that position.

Requirements
------------

Example
-------

This example adds a */createminigun* command to create a weapon that is always firing.

``` lua
function createMinigunWeapon()
    -- Create the weapon 1 meter above the player
    local x, y, z = getElementPosition(getLocalPlayer())
    local weapon = createWeapon("minigun", x, y, z + 1)
    -- Give it some ammo and fire it
    setWeaponClipAmmo(weapon, 99999)
    setWeaponState(weapon, "firing")

    -- Optionally adjust for model rotation (this value will be different for other weapons)
    setWeaponProperty(weapon, "fire_rotation", 0, -30, 0)
end
addCommandHandler("createminigun", createMinigunWeapon)
```

See also
--------

[ru:createWeapon](/docs/ru:createweapon.md "wikilink")
