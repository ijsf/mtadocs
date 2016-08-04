Use [ToggleControl](/docs/togglecontrol.md "wikilink") instead.

This function enables or disables the weapons on a vehicle

Syntax
------

``` lua
bool setVehicleGunsEnabled ( vehicle theVehicle, bool gunsEnabled )
```

### Required Arguments

-   **theVehicle**: The [element](/docs/element.md "wikilink") representing the [vehicle](/docs/vehicle.md "wikilink") whose guns you want to toggle.
-   **gunsEnabled**: A bool representing whether guns are enabled or disabled. *false* will disable them, *true* will enable them.

### Returns

Returns *true* if the guns were toggled succesfully, *false* if arguments passed were invalid.

Example
-------

<section name="Example 1" class="server" show="true">
This function will disables the ability to fire rockets on a hydra.

``` lua
function disableFireForHydra ( theVehicle, seat, jacked )
    if ( getElementModel ( theVehicle ) == 520 ) then -- if they entered a hydra
        setVehicleGunsEnabled ( theVehicle, false ) -- disable their guns
    else -- if they entered another vehicle
        setVehicleGunsEnabled ( theVehicle, true ) -- enable their guns
    end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), disableFireForHydra )
```

</section>
<section name="Example 2" class="client" show="false">
This function will disables the ability to fire rockets on a hydra.

``` lua
function disableFireForHydra ( theVehicle, seat )
    if ( getElementModel ( theVehicle ) == 520 ) then -- if they entered a hydra
        setVehicleGunsEnabled ( theVehicle, false ) -- disable their guns
    else -- if they entered another vehicle
        setVehicleGunsEnabled ( theVehicle, true ) -- enable their guns
    end
end
addEventHandler ( "onClientPlayerEnterVehicle", getLocalPlayer(), disableFireForHydra )
```

</section>
See Also
--------
