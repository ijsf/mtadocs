Syntax
------

``` lua
bool setTrainTrack ( vehicle train, int track )
```

### Required Arguments

-   **train:** the train of which to set the track
-   **track:** the track where you want to set the train. It can be 0, 1, 2 or 3.

### Returns

Returns *true* if the track was set to the train, *false* otherwise.

Example
-------

This server-side script allows the player to change the track of their train.

<section name="Procedural" class="server">
``` lua
addCommandHandler("trackies",
    function (player, _, track)
        local theVehicle = getPedOccupiedVehicle(player)
        if not theVehicle then
            outputChatBox("You are not in a vehicle!")
            return
        end

        if getVehicleType(theVehicle) == "Train" then
            setTrainTrack(theVehicle, track)
        else
            outputChatBox("You are not in a train!")
        end
    end
)
```

</section>
<section name="Object Oriented" class="server">
``` lua
addCommandHandler("trackies",
    function (player, _, track)
        local veh = player.vehicle
        if not veh then
            return outputChatBox("You are not in a vehicle!")
        end

        if veh.vehicleType == "Train" then
            veh.track = track
        else
            outputChatBox("You are not in a train!")
        end
    end
)
```

</section>
See Also
--------
