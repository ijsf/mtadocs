giveWeaponAmmo gives a specified ammount of ammo to a certain player, for a specified weapon (if they already have it).

Syntax
------

``` lua
 bool giveWeaponAmmo ( player thePlayer, int weapon, int ammo )
```

### Required Arguments

-   **thePlayer:** A [player](/player.md "wikilink") object referencing the specified player
-   **weapon:** A whole number integer that refers to a [weapon](/weapon.md "wikilink") ID.
-   **ammo:** A whole number integer serving as the ammo amount for the given weapon

Returns
-------

Returns a boolean value *true* or *false* that tells you if it was successful or not.

Example
-------

This example will give players an M4 weapon with 200 ammo followed by 5 more ammo when they spawn.

``` lua
function scriptOnSpawnpointUse ( thePlayer )
    giveWeapon ( thePlayer, 31, 200 ) -- Gives the M4 weapon with 200 ammo to any player when they use a spawnpoint
    giveWeaponAmmo ( thePlayer, 31, 5 ) -- Gives the player 5 more ammo for the M4
end
addEventHandler ( "onSpawnpointUse", getRootElement(), onSpawnpointUse )
```

See Also
--------

[ru:giveWeaponAmmo](/ru:giveWeaponAmmo.md "wikilink")
