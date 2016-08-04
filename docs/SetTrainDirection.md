Sets the direction in which a train or tram drives over the rails (clockwise or counterclockwise).

Syntax
------

``` lua
bool setTrainDirection ( vehicle train, bool clockwise )
```

### Required Arguments

-   **train:** the train whose direction to change.
-   **clockwise:** if *true*, will make the train go clockwise. If *false*, makes it go counterclockwise.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

This function will make a train driving clockwise.


    function createTrain(source)
        local myTrain = createVehicle(537,1995,-1949,13)  -- Create the train
        setTrainDirection(myTrain, true) -- Make the train drive clockwise
            setTrainSpeed(myTrain, 1) -- Speed up
    end
    addCommandHandler("mytrain", createTrain)

See Also
--------
