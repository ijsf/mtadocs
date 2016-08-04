This function will set a train or tram as derailed.

Syntax
------

``` lua
bool setTrainDerailed ( vehicle vehicleToDerail, bool derailed )              
```

### Required Arguments

-   **vehicleToDerail:** The vehicle that you wish to derail.
-   **derailed:** whether the train is derailed.

### Returns

Returns *true* if the state was successfully set

Example
-------

<section name="Example" class="server" show="true">
This example creates an underailable train, and allows it to be derailed when you want

``` lua
function makeTrain(thePlayer)
    myTrain = createVehicle(537,1995,-1949,13)-- This will make a freight train just east of the LS train station
    setTrainDerailable(myTrain, false) -- myTrain can not be derailed now
    outputChatBox("A freight train has been created for you.", thePlayer) -- Just a simple message for the player
end
addCommandHandler("trainmeup", makeTrain)

function derailTrain()
    setTrainDerailed(myTrain, true) -- When the command is used the train becomes derailed
    outputChatBox("Freight train has been derailed!", thePlayer) -- A message to confirm the train was derailed
end
addCommandHandler("derailme", derailTrain)
```

</section>
See Also
--------
