This function will get the taxi light state of a taxi (vehicle IDs 420 and 438)

Syntax
------

``` lua
bool isVehicleTaxiLightOn ( vehicle taxi )              
```

### Required Arguments

-   **taxi:** The vehicle element of the taxi that you wish to get the light state of.

### Returns

Returns *true* if the light is on, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example binds the 'o' key to a function that toggles the taxi's light on and off, if you're in a taxi.

``` lua
function toggleTaxiLight()
   local thePlayer = getLocalPlayer()
   if isPedInVehicle(thePlayer) then
      local theVehicle = getPedOccupiedVehicle(thePlayer)
      if thePlayer == getVehicleOccupant(theVehicle, 0) then -- if is a driver
     local id = getElementModel(theVehicle) -- getting vehicle model
     if ((id == 420) or (id == 438)) then -- if is a taxi
        local lights = isVehicleTaxiLightOn(theVehicle) -- getting vehicle lights state
        setVehicleTaxiLightOn(theVehicle, not lights) -- switch lights
     end
      end   
   end
end
bindKey("o", "down", toggleTaxiLight) -- binding the function
```

</section>
See Also
--------
