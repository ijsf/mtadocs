Creates a SWAT rope like that of the rope in single player used by SWAT Teams abseiling from the Police Maverick.

Syntax
------

``` lua
bool createSWATRope ( float fx, float fy, float fZ, int duration )
```

### Required Arguments

-   **fx, fy, fz:** the world coordinates where the effect originates.
-   **duration:** the amount in miliseconds the rope will be there before falling to the ground.

Example
-------

This example creates a Swat rope in police maverick when you use the command /createrope

``` lua
function SwatRope()
    local myVehicle = getPedOccupiedVehicle(localPlayer)
    if myVehicle and getVehicleName(myVehicle) == "Police Maverick" then
        local x,y,z = getElementPosition(myVehicle)
        createSWATRope(x, y, z, 11111)  
    end
end
addCommandHandler("createrope", SwatRope)
```

Requirements
------------

See Also
--------
