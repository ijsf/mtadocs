This event is triggered when a vehicle respawns.

Parameters
----------

This event has no parameters.

Source
------

The source of this event is the vehicle that respawned.

Example
-------

This example outputs to the console that a vehicle has respawned.

``` lua
addEventHandler("onClientVehicleRespawn",root,function()
    outputConsole("A vehicle has respawned.")
end)
```

See Also
--------

### Client vehicle events

### Client event functions

[es:onClientVehicleRespawn](/docs/es:onClientVehicleRespawn.md "wikilink")
