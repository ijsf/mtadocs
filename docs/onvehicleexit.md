This event is triggered when a player leaves a vehicle.

Parameters
----------

``` lua
player thePlayer, int seat, player jacker
```

-   **thePlayer**: A player element representing the player who exited the vehicle
-   **seat**: An integer representing the seat in which the player exited from
-   **jacker**: A player element representing the player who jacked the driver

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [vehicle](/docs/vehicle.md "wikilink") that was exited.

Example
-------

This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off.

``` lua
function addHelmetOnEnter ( thePlayer, seat, jacked )
    if ( getElementModel ( source ) == 522 ) then -- if its a nrg
        addPedClothes ( thePlayer, "moto", "moto", 16 ) -- add the helmet
    end
end
addEventHandler ( "onVehicleEnter", getRootElement(), addHelmetOnEnter )

function removeHelmetOnExit ( thePlayer, seat, jacked )
    if ( getElementModel ( source ) == 522 ) then -- if its a nrg
        removePedClothes ( thePlayer, 16 ) -- remove the helmet
    end
end
addEventHandler ( "onVehicleExit", getRootElement(), removeHelmetOnExit )
```

Example 2
---------

This example will turn off a vehicle's engine when the driver gets out of the car.

``` lua
addEventHandler ( "onPlayerVehicleExit", getRootElement(), function(theVehicle, leftSeat, jackerPlayer)
    if leftSeat == 0 and not jackerPlayer then
       setVehicleEngineState( theVehicle, false)
    end
end)
```
