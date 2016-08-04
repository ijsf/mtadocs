<div style="background: #FF7070; border: 3px solid #FF0000;">
**Attention:** This event is not implemented in current builds.

</div>
This event is triggered when a vehicle starts to drown in water. This event is even triggered when vehicles merely come into contact with water, so not every trigger is an indication of actual drowning.

Parameters
----------

This event has no parameters.

Source
------

The source of this event is the [vehicle](/vehicle.md "wikilink") that is drowning.

Example
-------

``` lua
addEventHandler("onClientVehicleDrown",root,function()
     outputChatBox("* A "..getVehicleName(source).." is drowning!")
end)
```

See Also
--------

### Client vehicle events

### Client event functions
