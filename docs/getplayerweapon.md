This function tells you which weapon type is in the player's current slot (clientside, you can optionally specify a slot other than the current one). See [Weapon Info](/docs/weapon.md "wikilink")

Syntax
------

<section name="Server" class="server" show="true">
``` lua
int getPlayerWeapon ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: the [player](/docs/player.md "wikilink") you want to get the weapon type from.

### Returns

Returns an [int](/docs/int.md "wikilink") indicating the type of the weapon the player has currently equipped.

</section>
<section name="Client" class="client" show="true">
``` lua
int getPlayerWeapon ( player thePlayer, [ int weaponSlot = current ] )
```

### Required Arguments

-   **thePlayer**: the [player](/docs/player.md "wikilink") you want to get the weapon type from.

### Optional Arguments

-   **weaponSlot**: an integer representing the weapon slot (set to the players current slot if not given).

### Returns

Returns an [int](/docs/int.md "wikilink") indicating the type of the weapon the player has in the specified slot.

It should be noted that if a player runs out of ammo for a weapon, it will still return the ID of that weapon in the slot (even if it appears as if the player does not have a weapon at all), though [getPlayerTotalAmmo](/docs/getPlayerTotalAmmo.md "wikilink") will return **0**. Therefore, [getPlayerTotalAmmo](/getPlayerTotalAmmo.md "wikilink") should be used in conjunction with [getPlayerWeapon](/getPlayerWeapon.md "wikilink") in order to check if a player has a weapon.

</section>
Example
-------

<section name="Example" class="server" show="true">
This serverside example will display a player's current weapon type. In this case, it is hard coded to use the player called *someguy*.

``` lua
-- Find a player called someguy and find his current weapon id.
local weaponType = getPlayerWeapon ( getPlayerFromNick ( "someguy" ) )
-- If a weapon type was returned then
if ( weaponType ) then
  outputChatBox ( "someguy's current Weapon-type: " .. weaponType .. "." ) -- Display the weapon type in the chat box
end
```

</section>
See Also
--------
