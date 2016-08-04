Parameters
----------

``` lua
element theAttacker, int theWeapon, float loss, float damagePosX, float damagePosY, float damagePosZ, int tyreID
```

-   **theAttacker**: An element if there was an attacker.
-   **theWeapon**: An integer specifying the weapon ID if a weapon was used.
-   **loss**: A float representing the amount of damage taken.
-   **damagePosX**: A float representing the X co-ordinate of where the damage took place.
-   **damagePosY**: A float representing the Y co-ordinate of where the damage took place.
-   **damagePosZ**: A float representing the Z co-ordinate of where the damage took place.
-   **tyreID**: A number representing the tyre which took damage, if there is one.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [vehicle](/docs/vehicle.md "wikilink") that got damaged.

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the vehicle health won't be reduced. Physical damage to the vehicle will remain.

Example
-------

This example makes every SWAT tank immune from all weapon attacks.

<section name="Client" class="client" show="true">
``` lua
function handleVehicleDamage(attacker, weapon, loss, x, y, z, tyre)
    if (weapon and getElementModel(source) == 601) then
        -- A weapon was used and the vehicle model ID is that of the SWAT tank so cancel the damage.
        cancelEvent()
    end
end
addEventHandler("onClientVehicleDamage", root, handleVehicleDamage)
```

</section>
This example allows the Rhino to take damage from bullets even though they're bullet proof, this example doesn't work with explosions though.

<section name="Client" class="client" show="true">
``` lua
-- Only let these weapons damage a Rhino
local weaponsToDamageRhino = {
    [38] = true, -- minigun
    [33] = true, -- country rifle
    [34] = true, -- sniper rifle
    [30] = true, -- AK-47
    [31] = true, -- M4
}

function handleRhinoDamage(attacker, weapon, loss, x, y, z, tyre)
    if (weapon and getElementModel(source) == 432 and loss > 0) then
        if (weaponsToDamageRhino[weapon]) then
            setElementHealth(source, getElementHealth(source) - loss)
        end
    end
end
addEventHandler("onClientVehicleDamage", root, handleRhinoDamage)
```

</section>
This example will makes all vehicle Fireproof.

<section name="Client" class="client" show="true">
``` lua
function fireproofvehicle(theAttacker, theWeapon)
    if(theWeapon == 37) then
        cancelEvent()
    end
end
addEventHandler("onClientVehicleDamage", getRootElement(), fireproofvehicle)
```

</section>
See Also
--------

### Client vehicle events

### Client event functions
