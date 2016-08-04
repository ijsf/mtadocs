Sets a state of a specified player's control, as if they pressed or released it.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setControlState ( player thePlayer, string control, bool state ) 
```

### Required Arguments

-   **thePlayer:** The player you wish to set the control state of.
-   **control:** The control that you want to set the state of. See [control names](/docs/control_names.md "wikilink") for a list of possible controls.
-   **state:** A boolean value representing whether or not the key will be set to pressed or not.

</section>
<section name="Client" class="client" show="true">
``` lua
bool setControlState ( string control, bool state ) 
```

### Required Arguments

-   **control:** The control that you want to set the state of. See [control names](/docs/control_names.md "wikilink") for a list of possible controls.
-   **state:** A boolean value representing whether or not the key will be set to pressed or not.

</section>
### Returns

Returns *true* if the control state was successfully set, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example will disable the use of the accelerate, brake/reverse and handbrake keys, then force the accelerate on for any player who enters a vehicle.

``` lua
function onPlayerEnterVehicle ( theVehicle, seat, jacked )
    toggleControl ( source, "accelerate", false ) -- disable the accelerate key
    toggleControl ( source, "brake_reverse", false ) -- disable the brake_reverse key
    toggleControl ( source, "handbrake", false ) -- disable the handbrake key
    setControlState ( source, "accelerate", true ) -- force the accelerate key on
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), onPlayerEnterVehicle )
```

</section>
<section name="Client" class="client" show="true">
This example will disable the use of the accelerate, brake/reverse and handbrake keys, then force the accelerate on for any player who enters a vehicle.

``` lua

function onClientPlayerEnterVehicle ( theVehicle, seat, jacked )
    toggleControl ( "accelerate", false ) -- disable the accelerate key
    toggleControl ( "brake_reverse", false ) -- disable the brake_reverse key
    toggleControl ( "handbrake", false ) -- disable the handbrake key
    setControlState ( "accelerate", true ) -- force the accelerate key on
end
addEventHandler ( "onClientPlayerVehicleEnter", getRootElement(), onClientPlayerEnterVehicle )
```

</section>
See Also
--------
