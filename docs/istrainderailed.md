This function will check if a train or tram is derailed.

Syntax
------

``` lua
bool isTrainDerailed ( vehicle vehicleToCheck )              
```

### Required Arguments

-   **vehicleToCheck:** The vehicle that you wish to check is derailed.

### Returns

Returns *true* if the train is derailed, *false* if the train is still on the rails

Example
-------

<section name="Example" class="server" show="true">
This example lets a player check if the train they're driving has derailed.

``` lua
function checkDerailed(thePlayer)
    local theTrain = getPedOccupiedVehicle(thePlayer)
    if ( theTrain and getVehicleType(theTrain) == "Train" ) then --is the player in a vehicle and is it a train?
        if ( isTrainDerailed(theTrain) ) then --is the train derailed?
            outputChatBox("Your train is derailed", thePlayer, 255, 255, 0) --outputs a message
        else
            outputChatBox("Your train is not derailed", thePlayer, 0, 255, 0) --outputs a message
        end
    end
end
addCommandHandler("checkTrain", checkDerailed) --adds the command handler
```

</section>
See Also
--------
