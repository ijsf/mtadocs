This function retrieves the amount of ammo in a weapon pickup.

Syntax
------

``` lua
int getPickupAmmo ( pickup thePickup )         
```

### Required Arguments

-   **thePickup:** The pickup in which you wish to retrieve the ammo of

### Returns

Returns an *integer* of the amount of ammo in the pickup, *false* if the pickup element is invalid, 0 if it's no weapon pickup.

Example
-------

This example outputs a message with the picked up weapon and ammo to the player.

<section show="true" name="Server" class="server">
``` lua
function onPickupHitFunction ( thePlayer )
    if getPickupType ( source ) ~= 2 then return end   -- if the pickup is no weapon, stop
    local ammo = getPickupAmmo ( source )              -- get the amount of ammo
    local weapon = getPickupWeapon ( source )          -- get the weapon of the pickup
    outputChatBox ( "You just picked up a " .. getWeaponNameFromID(weapon) .. " with " .. ammo .. " ammo", thePlayer ) -- output a message to the player
end
addEventHandler ( "onPickupHit", getRootElement(), onPickupHitFunction ) -- add an event handler for onPickupHit
```

</section>
See Also
--------
