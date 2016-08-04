Syntax
------

``` lua
bool setVehicleNitroCount ( vehicle theVehicle, int count )
```

### Required Arguments

-   **theVehicle**: the [vehicle](/vehicle.md "wikilink") which you want to modify how many times a player can use its nitro.
-   **count**: how many times should the player be able to use the nitro of this [vehicle](/vehicle.md "wikilink") (from 0-100 times; 0 means that it can't be used and 101 means that it can be used infinite times).

### Returns

Returns *true* if the nitro count was set successfully to the vehicle, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This function installs nitro in the vehicle a player enters and then makes it usable only twice.

``` lua
function infiniteNitro(pPlayer)
    if pPlayer == localPlayer then
        if not getVehicleUpgradeOnSlot(source, 8) then -- Does the vehicle have nitro installed or not
            addVehicleUpgrade(source, 1010) -- Install nitrous
        end
        setVehicleNitroCount(source, 2) -- Make the nitro usable twice
    end
end
addEventHandler("onClientVehicleEnter", root, infiniteNitro)
```

</section>
Requirements
------------

See Also
--------
