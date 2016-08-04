This function will set the taxi light on in a taxi (vehicle ID's 420 and 438)

Syntax
------

``` lua
bool setVehicleTaxiLightOn ( vehicle taxi, bool LightState )              
```

### Required Arguments

-   **taxi:** The vehicle element of the taxi that you wish to turn the light on.
-   **LightState:** whether the light is on. *True* for on, *False* for off.

### Returns

Returns *true* if the state was successfully set, *false* otherwise.

Example
-------

This example sets the taxi light on when the player presses “o” in a taxi.

``` lua
addEventHandler ( "onPlayerJoin" , getRootElement ( ) , 
function ( )
  bindKey ( source , "o", "down", 
    function ( thePlayer )
      if ( isPedInVehicle ( thePlayer ) ) then --is in vehicle or not?
        local vehicle = getPedOccupiedVehicle ( thePlayer ) --getting player's occupied vehicle
        if ( getVehicleController ( vehicle ) == thePlayer ) then --is driver or not?
          local id = getElementModel ( vehicle ) --getting vehicle's model
          if ( ( id == 420 ) or ( id == 438 ) ) then --is a taxi?
            setVehicleTaxiLightOn ( vehicle, not isVehicleTaxiLightOn ( vehicle ) ) --changing taxi light on/off
          end
        end 
      end
   end)
end )
```

See Also
--------
