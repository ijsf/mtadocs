This function will set the headlight color of a vehicle. valid Red Green and Blue arguments range from 0-255

Syntax
------

``` lua
bool setVehicleHeadLightColor ( vehicle theVehicle, int red, int green, int blue)            
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") that you wish to set the headlight color of.
-   **red:** An integer indicating the amount of red for the vehicle's headlights
-   **green:** An integer indicating the amount of green for the vehicle's headlights
-   **blue:** An integer indicating the amount of blue for the vehicle's headlights

### Returns

Returns *true* if vehicle's headlight color was set, *false* if an invalid vehicle or invalid color ranges were specified for red,green or blue.

Example
-------

This example changes car lights color with command */carlights red\_color, green\_color, blue\_color*

It shows error if player isn't in vehicle or color failed to change. It shows a message if color changed successful.

``` lua
function changeCarLightsColor ( thePlayer, command, red, green, blue )
    local theVehicle = getPedOccupiedVehicle ( thePlayer )
    if ( not theVehicle ) then
        return outputChatBox( "You don't have vehicle!" )
    end
    red = tonumber ( red )
    green = tonumber ( green )
    blue = tonumber ( blue )
    -- check if the colour values for red, green and blue are valid
    if red and green and blue then
        local color = setVehicleHeadLightColor ( theVehicle, red, green, blue )
        if(not color) then
            outputChatBox( "Failed to change vehicle lights color" )
        else
            outputChatBox ( "Vehicle lights color changed sucessfully" )
        end
    else
        outputChatBox( "Failed to change vehicle lights color" )
    end
end
addCommandHandler ( "carlights", changeCarLightsColor )
```

See Also
--------
