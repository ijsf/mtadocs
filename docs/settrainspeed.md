Sets the on-track speed of a train.

Syntax
------

``` lua
bool setTrainSpeed ( vehicle train, float speed )
```

### Required Arguments

-   **train:** the train whose speed to change.
-   **speed:** the new on-track speed of the train. A positive value will make it go clockwise, a negative value counter clockwise.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Example" class="server" show="true">
This example will make a train east of LS station which can not be derailed, and start moving it.

``` lua
function makeTrain(source)
    local myTrain = createVehicle(537,1995,-1949,13)  -- This will make a freight train just east of the LS train station
    setTrainDerailable(myTrain, false) -- myTrain can not be derailed now
    outputChatBox("A freight train has been created for you.", source, 255, 255, 0) -- Just a simple message for the player
        warpPedIntoVehicle(source, myTrain) -- This will warp you to inside the train
        setTrainSpeed(myTrain, 1) -- Set the train speed to 1 - 100mph, 160kmh
end
addCommandHandler("trainmeup", makeTrain)
```

</section>
See Also
--------
