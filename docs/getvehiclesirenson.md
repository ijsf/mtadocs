This function returns whether the sirens are turned on for the specified vehicle.

Syntax
------

``` lua
bool getVehicleSirensOn ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle that will be checked.

### Returns

Returns *true* if the sirens are turned on for the specified vehicle, *false* if the sirens are turned off for the specified vehicle, if the vehicle doesn't have sirens or if invalid arguments are specified.

Example
-------

<section name="Server" class="server" show="true">
This example toggles siren state when a player enters a vehicle as a driver.

``` lua
function example_onVehicleEnter ( thePlayer, seat )
    --If the player entered as a driver
    if ( seat == 0 ) then
        --If siren was off
        if not getVehicleSirensOn ( source ) then
            setVehicleSirensOn ( source, true ) --Turn it on
        else
            setVehicleSirensOn ( source, false ) --Turn it off
        end
    end
end
addEventHandler ( "onVehicleEnter", getRootElement(), example_onVehicleEnter )
```

</section>
See Also
--------
