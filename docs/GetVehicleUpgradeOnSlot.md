Description
-----------

This function returns the current upgrade id on the specified vehicle's 'upgrade slot' An upgrade slot is a certain type of upgrade (eg: exhaust, spoiler), there are 17 slots (0 to 16).

Syntax
------

``` lua
int getVehicleUpgradeOnSlot ( vehicle theVehicle, int slot )
```

### Returns

Returns an *integer* with the upgrade on the slot if correct arguments were passed, *false* otherwise.

### Required Arguments

-   **theVehicle**: The [vehicle](/vehicle.md "wikilink") whose upgrade you want to retrieve.
-   **slot**: The slot id of the upgrade. *([Upgrade list](/Upgrade_list.md "wikilink") ordered by slot number)*

Example
-------

<section name="Server" class="server" show="true">
This example prints the name and upgrades on each slot of an entered vehicle to the chat.

``` lua
function scriptOnPlayerEnterVehicle ( theVehicle, seat, jacked )
    for i=0, 16 do
        local upgrade = getVehicleUpgradeOnSlot ( theVehicle, i )
        if ( upgrade ) then
            outputChatBox ( getVehicleUpgradeSlotName ( i ) .. ": " .. upgrade)
        end
    end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), scriptOnPlayerEnterVehicle )
```

</section>
See Also
--------
