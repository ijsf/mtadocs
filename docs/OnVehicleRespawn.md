This event is triggered when a vehicle is respawned due. See [toggleVehicleRespawn](/toggleVehicleRespawn.md "wikilink").

Parameters
----------

``` lua
bool exploded
```

-   **exploded**: *true* if this vehicle respawned because it exploded, *false* if it respawned due to being deserted.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [vehicle](/vehicle.md "wikilink") that respawned.

Example
-------

This example shows a message in the chatbox, if it is respawned.

``` lua
function onVehicleRespawn ( exploded )
  -- Add this variable. It contains the vehicle name of the respawned vehicle
  local vehicleName = getVehicleName ( source )
  
  -- If it is exploded, echo a custom message
  if ( exploded == true ) then 
    outputChatBox("A " .. vehiclename .. " has been respawned, after an explosion")
  
  -- else echo a normal message
  else 
    outputChatBox("A " .. vehiclename .. " has been respawned")
  end
end

-- Add the Event Handler
addEventHandler ( "onVehicleRespawn", getRootElement(), onVehicleRespawn )
```
