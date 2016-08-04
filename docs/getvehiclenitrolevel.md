Syntax
------

``` lua
float getVehicleNitroLevel ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle** The [vehicle](/docs/vehicle.md "wikilink"), which you want to get a nitro level.

### Returns

Returns *a float* determining the nitro level (ranges from 0.0001 to 1.0) of the vehicle, *false* if there is no nitro in the vehicle.

Example
-------

<section name="Client" class="client" show="true">
This function displays the nitro level of the vehicle the player is entering.

``` lua
function displayNitroLevel(pPlayer)
    if pPlayer == localPlayer then
        if getVehicleUpgradeOnSlot(source, 8) then -- Check if the vehicle has nitro installed
            local fNitroLevel = getVehicleNitroLevel(source)
            outputChatBox("The nitro level of this " .. getVehicleName(source) .. " is " .. fNitroLevel .. ".", 255, 180, 20, false)
        end
    end
end
addEventHandler("onClientVehicleEnter", root, displayNitroLevel)
```

</section>
Requirements
------------

See Also
--------
