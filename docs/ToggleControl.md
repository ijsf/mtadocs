Enables or disables the use of a GTA control for a specific player.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool toggleControl ( player thePlayer, string control, bool enabled ) 
```

### Required Arguments

-   **thePlayer:** The player you wish to toggle the control ability of.
-   **control:** The control that you want to toggle the ability of. See [control names](/control_names.md "wikilink") for a list of possible controls.
-   **enabled:** A boolean value representing whether or not the key will be usable or not.

</section>
<section name="Client" class="client" show="true">
``` lua
bool toggleControl ( string control, bool enabled ) 
```

### Required Arguments

-   **control:** The control that you want to toggle the ability of. See [control names](/control_names.md "wikilink") for a list of possible controls.
-   **enabled:** A boolean value representing whether or not the key will be usable or not.

</section>
Returns
-------

This function *true* if the control was set successfully, *false* otherwise.

Example
-------

<section name="Example 1" class="server" show="true">
This function will disable the use of the vehicle secondary-fire key for anyone in a Hydra, consequently removing the ability to fire rockets.

``` lua
function disableFireForHydra ( theVehicle, seat, jacked )
    if ( getElementModel ( theVehicle ) == 520 ) then -- if they entered a hydra
        toggleControl ( source, "vehicle_secondary_fire", false ) -- disable their fire key
    else -- if they entered another vehicle
        toggleControl ( source, "vehicle_secondary_fire", true ) -- enable their fire key
    end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), disableFireForHydra )
```

</section>
<section name="Example 2" class="client" show="true">
This function will disable the use of the vehicle secondary-fire key for anyone in a Hydra, consequently removing the ability to fire rockets.

``` lua
function disableFireForHydra ( theVehicle, seat )
    if ( getElementModel ( theVehicle ) == 520 ) then -- if they entered a hydra
        toggleControl ( "vehicle_secondary_fire", false ) -- disable their fire key
    else -- if they entered another vehicle
        toggleControl ( "vehicle_secondary_fire", true ) -- enable their fire key
    end
end
addEventHandler ( "onClientPlayerVehicleEnter", getLocalPlayer(), disableFireForHydra )
```

</section>
See Also
--------
