This function gets a weapon property of the specified [custom weapon](/docs/element/weapon.md "wikilink") (clientside only) or specified [player-held weapon](/docs/weapons.md "wikilink") (both client and server).

Syntax
------

``` lua
int getWeaponProperty ( int weaponID/string weaponName, string weaponSkill, string property )
```

Required Arguments
------------------

-   **weaponID or weaponName:** The ID or name of the weapon you want to get info of. Names can be:

-   **weaponSkill:** Either: “pro”, “std” or “poor”
-   **property:** The property you want to get the value of:

The following properties are get only:

Returns
-------

On success:

**int:** The weapon property

On failure:

**bool:** False if the passed arguments were invalid

Example
-------

This example gets the weapon range of the M4 at poor skill level

``` lua
local range = getWeaponProperty(31, "poor", "weapon_range")
outputChatBox("M4 range at poor is: "..tostring(range))
```

Requirements
------------

See also
--------
