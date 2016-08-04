Checks to see if a vehicle has contact with the ground.

Syntax
------

``` lua
bool isVehicleOnGround ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle you wish to check.

### Returns

Returns *true* if vehicle is on the ground, *false* if it is not.

Example
-------

This example tells you when you've jumped out of a vehicle.

<section name="Server" class="server" show="true">
``` lua
function checkVState ( vehicle, seat, jacked )
    vehName = getVehicleName ( vehicle )

    if isVehicleOnGround ( vehicle ) == false then
        outputChatBox ( "You jumped out of a "..vehName.."!", source, 255, 0, 0  )
    end

end
addEventHandler ( "onPlayerVehicleExit", getRootElement(), checkVState )
```

</section>
Issues
------

See Also
--------
