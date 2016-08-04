This event is triggered when a player leaves a vehicle, for whatever reason.

Parameters
----------

``` lua
vehicle theVehicle, int seat, player jacker
```

-   **theVehicle**: A vehicle element representing the vehicle in which the player exited from
-   **seat**: An integer representing the seat in which the player was before exiting
-   **jacker**: A player element representing the player who jacked the driver

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that left the vehicle.

Example
-------

This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off.

``` lua
function addHelmetOnEnter ( vehicle, seat, jacked )
  if ( getVehicleID ( vehicle ) == 522 ) then -- if its a nrg
    addPedClothes ( source, "moto", "moto", 16 ) -- add the helmet
  end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), addHelmetOnEnter )

function removeHelmetOnExit ( vehicle, seat, jacked )
  if ( getVehicleID ( vehicle ) == 522 ) then -- if its a nrg
    removePedClothes ( source, 16 ) -- remove the helmet
  end
end
addEventHandler ( "onPlayerVehicleExit", getRootElement(), removeHelmetOnExit )
```
