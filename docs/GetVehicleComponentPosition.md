This function get component position for [vehicle](/vehicle.md "wikilink").

Syntax
------

``` lua
float, float, float getVehicleComponentPosition ( vehicle theVehicle, string theComponent [, string base = "root"] )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") you wish to get component position.
-   **theComponent:** A vehicle component (this is the frame name from the model file of the component you wish to modify)

### Optional Arguments

### Returns

Returns three *floats* indicating the position of the component, *x*, *y* and *z* respectively.

Example
-------

This example gets the name and the position of the components and outputs it in the chat.

``` lua
addCommandHandler("vcp", -- short for 'vehicle component position'
    function()
        local theVeh = getPedOccupiedVehicle(localPlayer)
    local getComponent = getVehicleComponents(theVeh) -- returns table with all the components of the vehicle
        if (theVeh) then
            for k in pairs (getComponent) do
        local x, y, z = getVehicleComponentPosition(theVeh, k)
                outputChatBox("Position of "..k.." is"..x.." "..y.." "..z)
            end
        end
    end
)
```

Changelog
---------

See Also
--------
