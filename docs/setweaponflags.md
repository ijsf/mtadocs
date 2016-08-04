This function sets a [custom weapon](/docs/element/weapon.md "wikilink") flags, used to change how it behaves or finds a possible target to shoot.

Syntax
------

``` lua
bool setWeaponFlags ( weapon theWeapon, string theFlag, bool enable )
```

### Required Arguments

-   **theWeapon:** the [weapon element](/docs/element/weapon.md "wikilink") to set the flag of.
-   **theFlag:** the weapon flag to change (all of them can be *true* or *false*):
    -   **disable\_model**: makes the weapon and muzzle effect invisible or not.
    -   **flags**: configures the flags used to get where the gun shoots at. They are based on [processLineOfSight](/docs/processlineofsight.md "wikilink")'s. You have to specify all the eight flags for the function to succeed. These flags are (by order):
        -   **checkBuildings**: allows the shoot to be blocked by GTA's internally placed buildings, i.e. the world map.
        -   **checkCarTires**: allows the shoot to be blocked by [vehicle](/docs/vehicle.md "wikilink") tires.
        -   **checkDummies**: allows the shoot to be blocked by GTA's internal dummies. These are not used in the current MTA version so this argument can be set to *false*.
        -   **checkObjects**: allows the shoot to be blocked by [objects](/docs/object.md "wikilink").
        -   **checkPeds**: allows the shoot to be blocked by [peds](/docs/ped.md "wikilink") and [players](/player.md "wikilink").
        -   **checkVehicles**: allows the shoot to be blocked by [vehicles](/docs/vehicle.md "wikilink").
        -   **checkSeeThroughStuff**: allows the shoot to be blocked by translucent game objects, e.g. glass.
        -   **checkShootThroughStuff**: allows the shoot to be blocked by things that can be shot through.
    -   **instant\_reload**: if enabled, the weapon will reload instantly rather than waiting the reload time until shooting again.
    -   **shoot\_if\_out\_of\_range**: if enabled, the weapon will still fire its target beyond the weapon range distance.
    -   **shoot\_if\_blocked**: if enabled, the weapon will still fire its target even if it's blocked by something.
-   **enable**: whether to enable or disable the specified flag.

### Returns

Returns *true* if all arguments are valid and the flags where changed; *false* otherwise.

Example
-------

This example creates a minigun that will kill any player who approaches the center of the map, no matter if he takes cover or not.

    local function setupDeadlyWeapon()
        local weapon = createWeapon("minigun", 0, 0, 10) -- Create the minigun
        setWeaponTarget(weapon, localPlayer) -- Set the weapon target to the local player
        setWeaponFlags(weapon, "flags", false, false, false, false, false, false, false, false) -- Allow the weapon to shoot through everything
    end
    addEventHandler("onClientResourceStart", resourceRoot, setupDeadlyWeapon)

Requirements
------------

Issues
------

See also
--------
