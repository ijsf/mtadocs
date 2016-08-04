Syntax
------

``` lua
bool removeVehicleSirens ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle to remove the sirens of

### Returns

Returns *true* if sirens were successfully removed from the vehicle, *false* otherwise.

Example
-------

This example adds a vehicle siren on entering a vehicle and removes a vehicle siren on exiting.

``` lua
addEventHandler("onVehicleEnter",root,function(player,seat)
   if(player)and(seat==0)then
      addVehicleSirens(source,1,1)
   end
end)

addEventHandler("onVehicleExit",root,function(player,seat)
   if(player)and(seat==0)then
      removeVehicleSirens(source)
   end
end)
```

Requirements
------------

See Also
--------
