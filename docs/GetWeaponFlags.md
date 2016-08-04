This function gets the flags of a [custom weapon](/docs/Element/Weapon.md "wikilink").

Syntax
------

``` lua
bool getWeaponFlags ( weapon theWeapon, string theFlag )
```

### Required Arguments

-   **theWeapon:** the weapon to get the flag of.
-   **theFlag:** the weapon flag to get:
    -   **disable\_model**: makes the weapon and muzzle effect invisible or not.
    -   **flags**: returns the flags used to get where the gun shoots at. These flags are (by order):
        -   **checkBuildings**: allows the shoot to be blocked by GTA's internally placed buildings, i.e. the world map.
        -   **checkCarTires**: allows the shoot to be blocked by [vehicle](/docs/vehicle.md "wikilink") tires.
        -   **checkDummies**: allows the shoot to be blocked by GTA's internal dummies. These are not used in the current MTA version so this argument can be set to *false*.
        -   **checkObjects**: allows the shoot to be blocked by [objects](/docs/object.md "wikilink").
        -   **checkPeds**: allows the shoot to be blocked by [peds](/docs/ped.md "wikilink") and [players](/player.md "wikilink").
        -   **checkVehicles**: allows the shoot to be blocked by [vehicles](/docs/vehicle.md "wikilink").
        -   **checkSeeThroughStuff**: allows the shoot to be blocked by translucent game objects, e.g. glass.
        -   **checkShootThroughStuff**: allows the shoot to be blocked by things that can be shot through.
    -   **instant\_reload**: if enabled, the weapon reloads instantly rather than waiting the reload time until shooting again.
    -   **shoot\_if\_out\_of\_range**: if enabled, the weapon still fires its target beyond the weapon range distance.
    -   **shoot\_if\_blocked**: if enabled, the weapon still fires its target even if it's blocked by something.

### Returns

Returns the *true* or *false* on success (*flags* flag returns 8 values) if the flag is enabled or not. Returns *false* if the weapon element isn't valid or an error occured.

Example
-------

This example checks whether the instant\_reload flag is enabled or disabled.

``` lua
local weapon = createWeapon("silenced", 0, 0, 10) -- Create the weapon
if weapon then -- if the weapon exist then
   setWeaponFlags(weapon, "instant_reload", true) -- enable instant_reload
   local flag = (getWeaponFlags (weapon,"instant_reload") and "instant_reload enabled") or "instant_reload disabled"
   outputChatBox (flag)
end
```

Requirements
------------

See also
--------
