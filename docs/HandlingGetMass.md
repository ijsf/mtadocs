Returns the mass of a handling element or vehicle ID.

Syntax
------

``` lua
float handlingGetMass ( handling theHandling )
float handlingGetMass ( int vehicleID )
```

### Required Arguments

-   **theHandling:** the handling of which you want to get the mass, *or*
-   **vehicleID:** the vehicle ID of which you want to get the mass.

### Returns

If you specified a handling element, returns its mass if one is set, or *nil* otherwise. If you specified a vehicle ID, returns the mass that currently applies to vehicles of that ID. Returns *false* in case of failure.

Example
-------

``` lua
function getMass ( player, command )
local vehicle = getPedOccupiedVehicle(player)
    if vehicle then
      str = handlingGetMass(getElementModel(vehicle))
      outputChatBox("Your vehicle's handling mass is "..str,player,0,255,255)
    end
end
addCommandHandler ( "getmass", getMass )
```

See Also
--------
