Syntax
------

``` lua
bool resetVehicleComponentPosition ( vehicle theVehicle, string theComponent )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") you wish to reset component position.
-   **theComponent:** A vehicle component (this is the frame name from the model file of the component you wish to modify)

### Returns

Returns *true* if the position of the component was reset, *false* otherwise.

Example
-------

**Example 1:** This example would change the position of the component when the player enters a vehicle and resets it when you type /reset.

``` lua

addEventHandler("onClientVehicleEnter", getRootElement(),
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

addCommandHandler("reset",
    function()
        local theVeh = getPedOccupiedVehicle(localPlayer)
        local getComponent = getVehicleComponents(theVeh) -- returns table with all the components of the vehicle
        if (theVeh) then
        for k in pairs (getComponent) do
                resetVehicleComponentPosition(theVeh, k) -- resets the position of the component
        end
        end
    end
)
```

See Also
--------
