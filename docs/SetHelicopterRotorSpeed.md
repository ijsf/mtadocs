Sets the rotor speed of a helicopter.

Syntax
------

``` lua
bool setHelicopterRotorSpeed ( vehicle heli, float speed )
```

### Required Arguments

-   **heli:** the helicopter to adjust the rotor of.
-   **speed:** the new rotor speed. Usual values are 0 if the helicopter stands still, or 0.2 if the rotor is fully spun up. Higher values than normal will not affect the helicopter's handling. Negative values are allowed and will make the rotor spin in the opposite direction (pushing the helicopter down).

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

This example change the helicopter rotor speed.

<section name="Client" class="client" show="true">
``` lua
function rotorSpeed() 
   local theVehicle = getPedOccupiedVehicle (localPlayer)
     if theVehicle then 
    local controller = getVehicleController (theVehicle)
    if controller == localPlayer then 
       local vehecileType = getVehicleType(theVehicle)
       if vehecileType == "Helicopter" then 
        setHelicopterRotorSpeed (theVehicle,10)
       end 
       end 
   end 
end 
addCommandHandler("rs",rotorSpeed)
```

</section>
See Also
--------
