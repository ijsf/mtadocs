Returns the drag coefficient (amount of air resistance) of a handling element or a vehicle ID.

Syntax
------

``` lua
float handlingGetDragCoefficiency ( handling theHandling )
float handlingGetDragCoefficiency ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling you wish to get the drag coefficient of, *or*
-   **vehicleID:** the vehicle ID you wish to get the drag coefficient of.

### Returns

If you specified a handling element, returns its drag coefficient if one was set, or *nil* otherwise. If you specified a (valid) vehicle ID, returns the drag coefficient that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
function getDragCoefficiency ( player, command )
local vehicle = getPedOccupiedVehicle(player)
    if vehicle then
      str = handlingGetDragCoefficiency(getElementModel(vehicle))
      outputChatBox("Your vehicle's handling drag coefficiency is "..str,player,0,255,255)
    end
end
addCommandHandler ( "dragcoe", getDragCoefficiency )
```

See Also
--------
