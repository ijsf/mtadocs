Syntax
------

``` lua
bool setVehicleComponentPosition ( vehicle theVehicle, string theComponent, float posX, float posY, float posZ [, string base = "root"] )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") you wish to set component position.
-   **theComponent:** A vehicle component (this is the frame name from the model file of the component you wish to modify)
-   **posX:** The x position of this component from the center of the vehicle.
-   **posY:** The y position of this component from the center of the vehicle.
-   **posZ:** The z position of this component from the center of the vehicle.

### Optional Arguments

### Returns

Return *true* if component position was set successfully, *false* otherwise.

Example
-------

**Example 1:** This example would set the position of the component.

``` lua
addCommandHandler("scp", -- short for 'set component position'
    function()
        local theVeh = getPedOccupiedVehicle(localPlayer)
    local getComponent = getVehicleComponents(theVeh) -- returns table with all the components of the vehicle
        if (theVeh) then
            for k in pairs (getComponent) do
        local x, y, z = getVehicleComponentPosition(theVeh, k) --get the position of the component
                setVehicleComponentPosition(theVeh, k, x+1, y+1, z+1) -- increases by 1 unit
            end
        end
    end
)
```

Changelog
---------

See Also
--------
