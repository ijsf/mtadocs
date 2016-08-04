This function is used for adjusting the movable parts of a model, for example hydra jets or dump truck tray. This function only works on vehicles with adjustable properties.

Syntax
------

``` lua
bool setVehicleAdjustableProperty ( element theVehicle, int value )
```

### Required Arguments

-   **theVehicle**: The vehicle you wish to change the adjustable property of.
-   **value**: A value from 0 between ?. (Set the adjustable value between 0 and N. 0 is the default value. It is possible to force the setting beyond default maximum, for example setting above 5000 on the dump truck (normal max 2500) will cause the tray to be fully vertical.)

### Returns

Returns true if the adjustable property was set, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This clientside function allows the user to set the vehicle adjustable property of a vehicle that the user is in by typing a command:

``` lua
function adjustProperty ( command, adjustValue )
    --First check if our player is in a vehicle (otherwise there is nothing to adjust)
    if isPedInVehicle (getLocalPlayer()) then
        --Next check if there is a property to adjust on this vehicle that our player is in
        if getVehicleAdjustableProperty(getPedOccupiedVehicle(getLocalPlayer())) then
            --Set the vehicle property to the argument that was given with the command (adjustValue)
            setVehicleAdjustableProperty (getPedOccupiedVehicle(getLocalPlayer()), adjustValue )
        else
            outputChatBox("You are in a vehicle that has no adjustable property!")
        end
    else
        outputChatBox("You are not in a vehicle!")
    end
end
addCommandHandler ( "adjust", adjustProperty )
```

</section>
See Also
--------
