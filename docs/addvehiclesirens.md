Syntax
------

``` lua
bool addVehicleSirens ( vehicle theVehicle, int sirenCount, int sirenType, [bool 360flag = false, bool checkLosFlag = true, bool useRandomiser flag = true, bool silentFlag = false )
```

### Required Arguments

-   **theVehicle:** The vehicle to add sirens
-   **sirenCount:** The amount of siren points on the vehicle (8 maximum)
-   **sirenType:** An integer between 1 and 6 (1: invisible, 2: single, 3+: dual)

### Optional Arguments

-   **360flag:** Visible from all directions (applies to single type only)
-   **checkLosFlag:** Check line of sight between camera and light so it won't draw if blocked
-   **useRandomiser:** Randomise the light order, false for sequential
-   **silentFlag:** If you want the siren to be silent set this to true

### Returns

Returns *true* if sirens were successfully added to the vehicle, *false* otherwise.

Example
-------

This example adds a vehicle siren on entering a vehicle and removes a vehicle siren on exiting. (TESTED!)

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
