Syntax
------

``` lua
bool setVehicleNitroActivated ( vehicle theVehicle, bool state )
```

### Required Arguments

-   **theVehicle** The [vehicle](/vehicle.md "wikilink") to activate or deactivate the nitro on.
-   **state** *true* if you want to activate the nitro, *false* if you want to disable it.

### Returns

Returns *true* if the nitro activation state was modified successfully, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example adds and activates nitro in the vehicle the player enters.

``` lua
function activateNitro(pPlayer)
    if pPlayer == localPlayer then
        if not getVehicleUpgradeOnSlot(source, 8) then -- Check if the vehicle has nitro installed or not
            addVehicleUpgrade(source, 1010) -- Install the nitrous
        end
        setVehicleNitroActivated(source, true) -- Activate the nitro
    end
end
addEventHandler("onClientVehicleEnter", root, activateNitro) -- When the player enters a vehicle, it executes the function
```

</section>
Requirements
------------

See Also
--------
