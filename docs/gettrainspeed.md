Gets the speed at which a train is traveling on the rails.

Syntax
------

``` lua
float getTrainSpeed ( vehicle train )
```

### Required Arguments

-   **train:** the train of which to retrieve the speed.

### Returns

Returns the train's speed if successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example outputs how fast a player is going if they're in a train. The command is "/speed".

``` lua
function getPlayersTrainSpeed ( source, command ) -- Define source in the function header.
    if ( isPedInVehicle ( source ) ) -- Check if they're in a vehicle.
    local veh = getPedOccupiedVehicle ( source ) -- Get the vehicle they're in.
        if ( getVehicleType ( veh ) == "Train" ) then -- Check if the vehicle they're in is a train.
            local speed = getTrainSpeed ( veh ) -- Get the trains speed.
            outputChatBox ( "You are travelling at a speed of " .. speed, source, 255, 0, 0 ) -- Output their speed.
        else
            outputChatBox ( "You must be in a train to use this command.", source, 255, 0, 0 ) -- Tell them they're not in a train.
        end
    else
        outputChatBox ( "You must be in a train to use this command.", source, 255, 0, 0 ) -- Tell them they're not in a train.
    end
end
addCommandHandler ( "speed", getPlayersTrainSpeed ) -- Make the function trigger when a player types "/speed".
```

</section>
See Also
--------
