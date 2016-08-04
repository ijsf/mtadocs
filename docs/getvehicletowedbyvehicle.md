This function is used to get the vehicle being towed by another.

Syntax
------

``` lua
vehicle getVehicleTowedByVehicle ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/docs/vehicle.md "wikilink") you wish to get the towed vehicle from.

Returns
-------

Returns the vehicle that *theVehicle* is towing, *false* if it isn't towing a vehicle.

Example
-------

This example will create a trailer and a trailer-tower, attach them, then check if they attached.

``` lua
local towingVehicle = createVehicle ( 515, 500, 500, 40 ) -- create a trailer-tower (roadtrain)
local trailer = createVehicle ( 435, 500, 490, 40 ) -- create a trailer
attachTrailerToVehicle ( towingVehicle, trailer ) -- attach them
if ( getVehicleTowedByVehicle ( towingVehicle ) == trailer ) then -- if it attached
  outputChatBox ( "The vehicles were attached!" )
end
```

See Also
--------
