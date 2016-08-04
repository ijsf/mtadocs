takeWeaponAmmo takes a specified amount of ammo from a certain player, for a specified weapon (if they already have it).

Syntax
------

``` lua
takeWeaponAmmo ( player thePlayer, int weapon, int ammo )
```

### Required Arguments

-   **thePlayer:** A [player](/docs/player.md "wikilink") object referencing the specified player
-   **weapon:** A whole number integer that refers to a [weapon](/docs/weapon.md "wikilink") ID.
-   **ammo:** A whole number integer serving as the ammo amount for the given weapon

Example
-------

This example will give players an M4 weapon with 200 ammo followed by taking 5 ammo when they spawn.

``` lua
function onSpawnpointUse ( thePlayer )
    giveWeapon ( thePlayer, 31, 200 )    -- Gives the M4 weapon with 200 ammo to any player when they use a spawnpoint
    takeWeaponAmmo ( thePlayer, 31, 5 )  -- Takes 5 ammo from the player's M4
end
addEventHandler ( "onSpawnpointUse", getRootElement(), onSpawnpointUse )
```

See Also
--------

[ru:takeWeaponAmmo](/docs/ru:takeweaponammo.md "wikilink")
