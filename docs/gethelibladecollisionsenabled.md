This function gets the state of the helicopter blades collisions on the specified vehicle.

Syntax
------

``` lua
bool getHeliBladeCollisionsEnabled ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle that will be checked.

### Returns

Returns *true* if the collisions are enabled for specified vehicle, *false* if the collisions aren't enabled for the specified vehicle, if the vehicle is not a helicopter or if invalid arguments are specified.

Example
-------

<section name="Client" class="client" show="true">
This example shows the blade collisions state

``` lua
function onVehicleEnter ( seat, jacked )
    --If the player entered a helicopter
    if ( getVehicleType ( source ) == "Helicopter" ) then
        local state = getHeliBladeCollisionsEnabled‎(source )
        outputChatBox("Helicopter blades collisions are turned ".. (state and "on" or "off") )
    end
end
addEventHandler ( "onClientVehicleEnter", localPlayer, onVehicleEnter )
```

</section>
See Also
--------
