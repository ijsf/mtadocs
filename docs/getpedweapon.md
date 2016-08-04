This function tells you which weapon type is in a certain weapon slot of a ped. See [Weapon Info](/docs/weapon.md "wikilink")

Syntax
------

``` lua
int getPedWeapon ( ped thePed, [ int weaponSlot = current ] )
```

### Required Arguments

-   **thePed**: the [ped](/docs/ped.md "wikilink") you want to get the weapon type from.

### Optional Arguments

-   **weaponSlot**: an integer representing the weapon slot (set to the ped's current slot if not given).

### Returns

Returns an [int](/docs/int.md "wikilink") indicating the type of the weapon the ped has in the specified slot. If the slot is empty, it returns 0.

It should be noted that if a ped runs out of ammo for a weapon, it will still return the ID of that weapon in the slot (even if it appears as if the ped does not have a weapon at all), though [getPedTotalAmmo](/docs/getPedTotalAmmo.md "wikilink") will return **0**. Therefore, [getPedTotalAmmo](/getPedTotalAmmo.md "wikilink") should be used in conjunction with [getPedWeapon](/getPedWeapon.md "wikilink") in order to check if a ped has a weapon.

Example
-------

This example will display a player's current weapon type. In this case,a random player.

<section name="Server" class="server" show="true">
``` lua
-- Find a player called someguy and find his current weapon id.
local weaponType = getPedWeapon ( getRandomPlayer() )
-- If a weapon type was returned then
if ( weaponType ) then
    outputChatBox ( "someguy's current Weapon-type: " .. weaponType .. "." ) -- Display the weapon type in the chat box
end
```

</section>
See Also
--------
