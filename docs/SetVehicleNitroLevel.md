Syntax
------

``` lua
bool setVehicleNitroLevel ( vehicle theVehicle, float level )
```

### Required Arguments

-   **theVehicle** The [vehicle](/vehicle.md "wikilink"), which you want to set.
-   **level** Nitro level you want to set (ranges from 0.0001 to 1.0).

### Returns

Returns *true* if the nitro level was set successfully to the vehicle, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This function installs nitrous to the vehicle and sets the level of it to 0.1 when a player enters the vehicle.

``` lua
function changeNitroLevel(pPlayer)
    if pPlayer == localPlayer then
        if not getVehicleUpgradeOnSlot(source, 8) then -- Check if the vehicle has nitro in it or not
            addVehicleUpgrade(source, 1010) -- Install nitrous
        end
        setVehicleNitroLevel(source, 0.1) -- Set a nitro level of 0.1 to the vehicle
    end
end
addEventHandler("onClientVehicleEnter", root, changeNitroLevel)
```

</section>
Requirements
------------

See Also
--------
