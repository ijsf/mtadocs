This function returns an integer that contains the total ammo in a specified [ped](/ped.md "wikilink")'s weapon. See [Weapon Info](/weapon.md "wikilink")

Syntax
------

``` lua
int getPedTotalAmmo ( ped thePed, [ int weaponSlot = current ] )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") whose ammo you want to check.

### Optional Arguments

-   **weaponSlot**: an integer representing the weapon slot (set to the ped's current slot if not given)

### Returns

Returns an [int](/int.md "wikilink") containing the total amount of ammo for the specified ped's weapon, or 0 if the ped specified is invalid.

Example
-------

This example outputs the total amount of ammo a player called *Someguy* has for his weapon.

``` lua
-- Find the player called 'Someguy'
myPlayer = getPlayerFromName ( "Someguy" )
-- If a player called 'Someguy' was found then
if ( myPlayer ) then
    -- Retrieve the total amount of ammo for that player, and store it in a variable called 'ammo'
    ammo = getPedTotalAmmo ( myPlayer )
    -- Tell all the players how much ammo 'Someguy' has
    outputChatBox ( "Someguy's current total ammo: " .. ammo .. "." )
end
```

Issues
------

See Also
--------
