This function retrieves the weapon ID of a weapon pickup.

Syntax
------

``` lua
int getPickupWeapon ( pickup thePickup )         
```

### Required Arguments

-   **thePickup:** The pickup of which you wish to retrieve the weapon

### Returns

Returns the [Weapon ID](/docs/weapons.md "wikilink") of the pickup, or *false* if the pickup is invalid.

Example
-------

This example gives extra ammo to a player if a pickup only has a small amount of ammo.

<section name="Server" class="server" show="true">
``` lua
function onPickupHitFunc ( thePlayer )                  -- when a pickup is hit
    if getPickupType ( source ) == 2 then               -- check if it's a weapon pickup
        local ammo = getPickupAmmo ( source )           -- get the pickup ammo
        if ammo < 50 then                               -- if ammo is less than 50
            local weapon = getPickupWeapon ( source )   -- store pickup weapon
            giveWeaponAmmo ( thePlayer, weapon, 50 )    -- give an extra 50 ammo
        end
    end
end
addEventHandler ( "onPickupHit", getRootElement(), onPickupHitFunc )    -- add the function as handler for onPickupHit
```

</section>
See Also
--------
