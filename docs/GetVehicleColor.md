This function returns the color of the specified vehicle. A vehicle can have up to four colors.

Syntax
------

``` lua
int int int int getVehicleColor ( vehicle theVehicle )             
```

### Required Arguments

-   **theVehicle:** the [vehicle](/vehicle.md "wikilink") element.

### Returns

Returns 4 [ints](/int.md "wikilink") indicating the color of the vehicle. Returns *false* if the vehicle doesn't exist.

Valid color ids:

Example
-------

<section name="Server" class="server" show="true">
This will output the 4 colors of any car that the player enters.

``` lua
function playerEnterVehicle ( theVehicle, seat, jacked )
    -- Get the colors of the car and store them to 4 seperate variables
    local color1, color2, color3, color4 = getVehicleColor ( theVehicle )
    -- Output the four retrieved car colors into the chatbox
    outputChatBox ( "Car color 1: " .. color1 )
    outputChatBox ( "Car color 2: " .. color2 )
    outputChatBox ( "Car color 3: " .. color3 )
    outputChatBox ( "Car color 4: " .. color4 )
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), playerEnterVehicle )
```

</section>
See Also
--------
