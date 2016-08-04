This event is triggered when a vehicle explodes.

Parameters
----------

This event has no parameters.

Source
------

The source of this event is the vehicle that exploded.

Example
-------

This example will output some text to chat on vehicle explosion

``` lua
addEventHandler("onClientVehicleExplode", getRootElement(), function()
  local modelname = getVehicleName(source)
  outputChatBox(modelname.." just exploded!")
end)
```

See Also
--------

### Client vehicle events

### Client event functions

[es:onClientVehicleExplode](/docs/es:onclientvehicleexplode.md "wikilink")
