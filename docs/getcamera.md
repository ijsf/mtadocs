Syntax
------

``` lua
element getCamera ()
```

### Returns

Returns an [element](/docs/element.md "wikilink") that corresponds to the game camera

Example
-------

This example attaches (fixes) the camera to a vehicle.

``` lua
local cam = getCamera()
setElementPosition( cam, 0,0,0 )  -- Clear camera target
local myVehicle = getPedOccupiedVehicle(localPlayer)
attachElements( cam, myVehicle, 0,-4,2, -20,0,0 )
```

See Also
--------
