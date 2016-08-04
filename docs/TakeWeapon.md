This function removes a specified weapon or ammo from a certain player's inventory.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **thePlayer**: A player object referencing the specified player.
-   **weaponId**: An integer that refers to a [weapon](/docs/weapon.md "wikilink") that you wish to remove.

### Optional Arguments

-   **ammo**: If used, this amount of ammo will be taken instead and the weapon will not be removed.

### Returns

Returns a *true* if the weapon/ammo was removed successfully, *false* otherwise.

Example
-------

This example removes teargas from player.

``` lua
addCommandHandler( 'rtear',
  function( thePlayer )
    takeWeapon( thePlayer, 17 )
  end
)
```

See Also
--------

[ru:takeWeapon](/docs/ru:takeWeapon.md "wikilink")
