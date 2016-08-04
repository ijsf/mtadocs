This function returns an integer that contains the total ammo in a specified [player](/player.md "wikilink")'s weapon. See [Weapon Info](/weapon.md "wikilink")

Syntax
------

<section name="Server" class="server" show="true">
``` lua
int getPlayerTotalAmmo ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") whose ammo you want to check.

### Returns

Returns an [int](/int.md "wikilink") containing the total amount of ammo for the player's current weapon.

</section>
<section name="Client" class="client" show="true">
``` lua
int getPlayerTotalAmmo ( player thePlayer [, int weaponSlot = current ] )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") whose ammo you want to check.

<!-- -->

-   **weaponSlot**: an integer representing the weapon slot (set to the players current slot if not given)

### Returns

Returns an [int](/int.md "wikilink") containing the total amount of ammo for the specified player's weapon, or 0 if the player specified is invalid.

</section>
Example
-------

This example outputs the total amount of ammo a player called *Someguy* has for his weapon.

``` lua
-- Find the player called 'Someguy'
myPlayer = getPlayerFromNick ( "Someguy" )
-- If a player called 'Someguy' was found then
if ( myPlayer ) then
    -- Retrieve the total amount of ammo for that player, and store it in a variable called 'ammo'
    ammo = getPlayerTotalAmmo ( myPlayer )
    -- Tell all the players how much ammo 'Someguy' has
    outputChatBox ( "Someguy's current total ammo: " .. ammo .. "." )
end
```

See Also
--------
