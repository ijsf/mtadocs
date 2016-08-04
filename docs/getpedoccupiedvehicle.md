This function gets the [vehicle](/docs/vehicle.md "wikilink") that the ped is currently in or is trying to enter, if any.

Syntax
------

``` lua
vehicle getPedOccupiedVehicle ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/docs/ped.md "wikilink") whose vehicle you're looking up.

### Returns

Returns the vehicle that the specified ped is in, or *false* if the ped is not in a vehicle or is an invalid ped.

Example
-------

When a ped enters the 'getcarname' command and is currently in a vehicle, this example outputs the name of the vehicle.

``` lua
function showVehicleName ( thePlayer )
   local theVehicle = getPedOccupiedVehicle ( thePlayer )
   if theVehicle then
      outputChatBox ( "Name of the Vehicle: " .. getVehicleName ( theVehicle ), thePlayer )
   else
      outputChatBox ( "You do not have a Vehicle!", thePlayer, 255, 0, 0, true )
   end
end
addCommandHandler ( "getcarname", showVehicleName )
```

See Also
--------
