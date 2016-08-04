Enables or disables the use of all GTA controls for a specified player.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
 ) 
```

### Required Arguments

-   **thePlayer:** The player you wish to toggle the control ability of.
-   **enabled:** A boolean value representing whether or not the controls will be usable.

### Optional Arguments

-   **gtaControls:** A boolean deciding whether the *enabled* parameter will affect GTA's internal controls.
-   **mtaControls:** A boolean deciding whether the *enabled* parameter will affect MTA's own controls., e.g. chatbox.

</section>
<section name="Client" class="client" show="true">
``` lua
 ) 
```

### Required Arguments

-   **enabled:** A boolean value representing whether or not the controls will be usable.

### Optional Arguments

-   **gtaControls:** A boolean deciding whether the *enabled* parameter will affect GTA's internal controls.
-   **mtaControls:** A boolean deciding whether the *enabled* parameter will affect MTA's own controls., e.g. chatbox.

</section>
### Returns

This function returns *true* if controls were toggled successfully, false otherwise.

Example
-------

<section name="Server" class="server" show="true">
This function will disable the use of all controls in order to freeze a player, which will be used every time someone enters a vehicle.

``` lua
function freezeThisDude ( thePlayer, freezeTime )
    toggleAllControls ( thePlayer, false )                         -- disable this player's controls
    setTimer ( toggleAllControls, freezeTime, 1, thePlayer, true ) -- enable this player's controls after the specified time
end

function freezeOnEnterVehicle ( theVehicle, seat, jacked )
    freezeThisDude ( source, 5000 ) -- 'freeze' him for 5000ms = 5 seconds
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), freezeOnEnterVehicle )
```

</section>
See Also
--------
