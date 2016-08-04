This function makes a vehicle's doors undamageable, so they won't fall off when they're hit. Note that the vehicle **has** to be locked using [setVehicleLocked](/docs/setVehicleLocked.md "wikilink") for this setting to have any effect.

Syntax
------

``` lua
bool setVehicleDoorsUndamageable ( vehicle theVehicle, bool state )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") of which you wish to set the car door damageability.
-   **state:** A boolean denoting whether the vehicle's doors are undamageable (*true*) or damageable (*false*).

### Returns

Returns *true* if the damageability state was successfully changed, *false* if invalid arguments were passed.

Example
-------

Here you can disable all vehicles doors damage with /nodamage, and enable it with /adddamage.

``` lua
function doorsLikeGod()
    for i, car in ipairs( getElementsByType ("vehicle") ) do
        setVehicleDoorsUndamageable ( car, true )
    end
    outputChatBox("All vehicles doors is not damageable")
end
addCommandHandler("nodamage", doorsLikeGod)

function doorsNotLikeGod()
    for i, car in ipairs( getElementsByType ("vehicle") ) do
        setVehicleDoorsUndamageable ( car, false )
    end
    outputChatBox("Now everyone can kick vehicles doors and throw them away.")
end
addCommandHandler("adddamage", doorsNotLikeGod)
```

See Also
--------
