This function is used to get the vehicle that is towing another.

Syntax
------

``` lua
vehicle getVehicleTowingVehicle ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle**: the [vehicle](/vehicle.md "wikilink") being towed.

Returns
-------

-   The vehicle that *theVehicle* is being towed by.
-   *false* if it isn't being towed.

Example
-------

This example will create a trailer and a trailer-tower, attach them, then check if they attached.

``` lua
local towingVehicle = createVehicle ( 515, 500, 500, 40 ) -- create a trailer-tower (roadtrain)
local trailer = createVehicle ( 435, 500, 490, 40 ) -- create a trailer
attachTrailerToVehicle ( towingVehicle, trailer ) -- attach them
if ( getVehicleTowingVehicle ( trailer ) == towingVehicle ) then -- if it attached
  outputChatBox ( "The vehicles were attached!" )
end
```

See Also
--------
