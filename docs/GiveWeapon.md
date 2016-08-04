giveWeapon gives a specified weapon to a certain player or ped. There is an optional argument to specify ammunition. For example, a melee weapon doesn't need an ammo argument.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **thePlayer:** A [player](/player.md "wikilink") or [ped](/ped.md "wikilink") object referencing the specified player (or [ped](/ped.md "wikilink"))
-   **weapon:** A whole number integer that refers to a [Weapon](/Weapon.md "wikilink") ID. Click [here](/Weapon.md "wikilink") for a list of possible weapon IDs.

### Optional Arguments

-   **ammo:** A whole number integer serving as the ammo amount for the given weapon. For weapons that do not require ammo, such as melee, this should be at least 1.
-   **setAsCurrent:** A boolean value determining whether or not the weapon will be set as the players current.

### Returns

Returns *true* if weapon was successfully acquired, *false* otherwise.

Example
-------

**Example 1:** This example gives a player an M4 with 200 ammo whenever they spawn.

``` lua
function giveWeaponsOnSpawn ( theSpawnpont, theTeam )
    giveWeapon ( source, 31, 200 ) -- Gives the M4 weapon with 200 ammo
end
addEventHandler ( "onPlayerSpawn", getRootElement(), giveWeaponsOnSpawn ) -- attach the event handler
```

**Example 2:** This example adds a “give” command in console which allows giving of any weapon by entering “give <id> <amount>”.

``` lua
function consoleGive ( thePlayer, commandName, weaponID, ammo )
    local status = giveWeapon ( thePlayer, weaponID, ammo, true )   -- attempt to give the weapon, forcing it as selected weapon
    if ( not status ) then                                          -- if it was unsuccessful
        outputConsole ( "Failed to give weapon.", thePlayer )   -- tell the player
    end
end
addCommandHandler ( "give", consoleGive )
```

**Example 3:** This example creates a ped in certain coordinates. You can give him a weapon with “give <weaponID> <amount>” command in console.

``` lua
ped = createPed( 19, -1634.5775, 1203.85, 7.1796 )

addCommandHandler( "give",
  function ( player, command, id, amount )
    if not tonumber ( id ) then return end

    if not tonumber ( amount ) then
        amount = 9001
    end

    giveWeapon( ped, id, amount, true )
  end
)
```

See Also
--------

[ru:giveWeapon](/ru:giveWeapon.md "wikilink")
