This event is triggered when a trailer gets detached from its towing vehicle.

Parameters
----------

``` lua
vehicle towedBy
```

-   **towedBy:** the vehicle that was towing the trailer.

Source
------

The source of this event is the trailer that is now detached.

Example
-------

This example outputs to the player that's towing the trailer that “The vehicle is now detached”. (TESTED!)

``` lua
addEventHandler("onClientTrailerDetach",root,function(towedBy)
    player = getVehicleOccupant(towedBy,0)
    outputChatBox("The vehicle is now detached.",player)
end)
```

See Also
--------

### Client vehicle events

### Client event functions

[es:onClientTrailerDetach](/docs/es:onclienttrailerdetach.md "wikilink")
