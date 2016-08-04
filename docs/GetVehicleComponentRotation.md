This function get component rotation for [vehicle](/docs/vehicle.md "wikilink").

Syntax
------

``` lua
float, float, float getVehicleComponentRotation ( vehicle theVehicle, string theComponent [, string base = "parent"] )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") you wish to get component rotation.
-   **theComponent:** A vehicle component (this is the frame name from the model file of the component you wish to modify)

### Optional Arguments

### Returns

Returns three *floats* indicating the rotation of the component, *x*, *y* and *z* respectively.

Example
-------

**Example 1:** This example would get the name and the position of the components and output it in the chat.

``` lua
addCommandHandler("vcr", -- short for 'vehicle component rotation'
    function()
        local theVeh = getPedOccupiedVehicle(localPlayer)
    local getComponent = getVehicleComponents(theVeh) -- returns table with all the components of the vehicle
        if (theVeh) then
            for k in pairs (getComponent) do
        local rx, ry, rz = getVehicleComponentRotation(theVeh, k)
                outputChatBox("Rotation of "..k.." is "..rx.." "..ry.." "..rz)
            end
        end
    end
)
```

Changelog
---------

See Also
--------
