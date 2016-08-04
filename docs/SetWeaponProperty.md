<section name="setWeaponProperty" class="server" show="true">
This function sets the weapon property of the specified weapons specified weapon type. See lower down the page for documentation related to weapon creation.

Syntax
------

``` lua
bool setWeaponProperty ( int weaponID/string weaponName, string weaponSkill, string property, int/float theValue )
```

Required Arguments
------------------

-   **weaponID:** The ID or name of the [weapon](/Weapons.md "wikilink") you want to set a property of. Names can be:

-   **weaponSkill:** Either: “pro”, “std” or “poor”. The player must have this skill level set to have the effect.
-   **property:** The property you want to set the value of:

-   **theValue:** The value to set the property to.

Returns
-------

On success:

**bool:** Returns true if the weapon property was successfully set

On failure:

**bool:** Returns false if the weapon property was unable to be set

Example
-------

This example sets the weapon range of the M4 at poor skill level to 75

``` lua
local rangeSet = setWeaponProperty(31, "poor", "weapon_range", 75)
if (rangeSet) then
    outputChatBox("M4 range at poor skill is set now 75!")
end
```

This example makes the silenced pistol dual wielded at pro skill level

``` lua
setWeaponProperty(23, "pro", "flags", 0x000800) -- Warning - Depends on the current flag setting
setWeaponProperty(23, "pro", "flags", 0x000002) -- Warning - Depends on the current flag setting
setWeaponProperty(23, "pro", "maximum_clip_ammo", 34)
```

This examples doubles the range of the colt 45 hand gun

``` lua
setWeaponProperty(22, "poor", "weapon_range", 70)
setWeaponProperty(22, "std", "weapon_range", 70)
setWeaponProperty(22, "pro", "weapon_range", 70)
```

This example makes the minigun able to fire all its ammo without the short reload time

``` lua
setWeaponProperty("minigun", "pro", "maximum_clip_ammo", 1000)
```

This example turns off auto aim for all weapons

``` lua
function setAutoAimForAllWeapons( bEnable )
    weaponList = { "colt 45", "silenced", "deagle", "shotgun", "sawed-off", "combat shotgun", "uzi", "mp5", "ak-47", "m4", "tec-9", "rifle", "sniper", "minigun" }
    for _,weapon in ipairs( weaponList ) do
        for _,skill in ipairs( { "poor", "std", "pro" } ) do
            setWeaponPropertyFlag( weapon, skill, 0x0001, not bEnable )
        end
    end
end

-- Set or clear an individual weapon flag bit
function setWeaponPropertyFlag( weapon, skill, flagBit, bSet )
    local bIsSet = bitAnd( getWeaponProperty(weapon, skill, "flags"), flagBit ) ~= 0
    if bIsSet ~= bSet then
        setWeaponProperty(weapon, skill, "flags", flagBit)
    end
end

-- Turn off auto aim
setAutoAimForAllWeapons( false )
```

Requirements
------------

</section>
<section name="setWeaponProperty" class="client" show="true">
Syntax (custom weapons)
-----------------------

``` lua
bool setWeaponProperty ( weapon theWeapon, string strProperty, value theValue )
```

Required Arguments
------------------

-   **theWeapon:** the weapon to change the property of.
-   **strProperty:** the property to edit:

-   **theValue:** The value to set the property to.

Returns
-------

Returns *true* if the property was set.

Requirements
------------

Changelog
---------

</section>
See also
--------
