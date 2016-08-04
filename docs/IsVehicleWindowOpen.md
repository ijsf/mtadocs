Syntax
------

``` lua
bool isVehicleWindowOpen ( vehicle theVehicle, int window )
```

### Required arguments

-   **theVehicle:** The vehicle that you wish to get the window state.
-   **window:** An [integer](/docs/int.md "wikilink") representing a vehicle window. It can be:
    -   **0:** motorbike shield
    -   **1:** rear window
    -   **2:** right front window
    -   **3:** right back window
    -   **4:** left front (driver) window
    -   **5:** left back window
    -   **6:** windshield

Returns
-------

This function returns a boolean which represents window open state.

Example
-------

This example opens the vehicle windows when the local player use /openwindow <window number>.

``` lua
function openVehicleWindow (cmd,number)
   if (isPedInVehicle (localPlayer)) then
      local vehicle = getPedOccupiedVehicle(localPlayer) 
      if number and tonumber(number) then
     if tonumber(number) > 0 and tonumber(number) < 7 then
        setVehicleWindowOpen(vehicle,tonumber(number), not isVehicleWindowOpen( vehicle, tonumber(number)))
     end
      end
   end
end
addCommandHandler ("openwindow",openVehicleWindow)
```

See also
--------
