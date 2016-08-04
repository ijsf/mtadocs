This function gets the original weapon property of the specified weapons specified weapon type.

Syntax
------

``` lua
int getOriginalWeaponProperty ( int weaponID/string weaponName, string weaponSkill, string property )
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

This example gets the default weapon range of the M4 at poor skill level

``` lua
local range = getOriginalWeaponProperty(31, "poor", "weapon_range")
outputChatBox("Default M4 range at poor is: "..tostring(range))
```

Requirements
------------

See Also
--------
