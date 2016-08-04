This function retrieves the ID of a vehicle as an integer value.

Syntax
------

``` lua
int getVehicleID ( vehicle theVehicle )             
```

### Required Arguments

-   **theVehicle:** The vehicle you want to get the ID of.

### Returns

Returns an integer containing the requested vehicle's ID, or false if the vehicle passed to the function is invalid.

Example
-------

``` lua
function planeEnter ( theVehicle, seat, jacked ) --when someone enters a vehicle
  id = getVehicleID ( theVehicle ) -- get the ID of the vehicle
  if id == 519 or id == 577 then --if theVehicle is one of these two planes
     vehiclename = getVehicleName ( theVehicle ) -- define the vehicle name 
     outputChatBox ( "Someone stole a " .. vehiclename .. "!" ) -- announce that someone stole the plane
  end
end
-- add the event to the event handler
addEventHandler ( "onPlayerEnterVehicle", getRootElement(), planeEnter )
```

See Also
--------
