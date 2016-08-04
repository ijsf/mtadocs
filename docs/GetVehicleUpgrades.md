This function returns a table of all the upgrades on a specifed vehicle.

Syntax
------

``` lua
table getVehicleUpgrades ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") you wish to retrieve the upgrades of.

### Returns

Returns a *table* of all the upgrades on each slot of a vehicle, which may be empty, or *false* if a valid vehicle is not passed.

Example
-------

<section name="Server" class="server" show="true">
This example prints the name and upgrades on each slot of an entered vehicle to the chat.

``` lua
function scriptOnPlayerEnterVehicle ( theVehicle, seat, jacked )
    local upgrades = getVehicleUpgrades ( theVehicle )
    for upgradeKey, upgradeValue in ipairs ( upgrades ) do
        outputChatBox ( getVehicleUpgradeSlotName ( upgradeKey - 1 ) .. ": " .. upgradeValue )
    end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), scriptOnPlayerEnterVehicle )
```

</section>
See Also
--------
