This function returns a table of all the compatible upgrades (or all for a specified slot, optionally) for a specifed vehicle.

Syntax
------

``` lua
table getVehicleCompatibleUpgrades ( vehicle theVehicle, [ int slot ] )
```

### Required Arguments

-   **theVehicle:** the [vehicle](/docs/vehicle.md "wikilink") you wish to retrieve the list of compatible upgrades of.

### Optional Arguments

-   **slot:** the upgrade slot number for which you're getting the list (from 0 to 16). Compatible upgrades for all slots are listed if this is not specified.

### Returns

Returns a *table* with all the compatible upgrades, or *false* if invalid arguments are passed.

Example
-------

This example displays a list of all the compatible upgrades for a vehicle when you enter it.

``` lua
function scriptOnPlayerEnterVehicle ( invehicle, seat, jacked )
  local upgrades = getVehicleCompatibleUpgrades ( invehicle )
  for upgradeKey, upgradeValue in ipairs ( upgrades ) do
    outputChatBox ( getVehicleUpgradeSlotName ( upgradeValue ) .. ": " .. upgradeValue )
  end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), scriptOnPlayerEnterVehicle )
```

See Also
--------
