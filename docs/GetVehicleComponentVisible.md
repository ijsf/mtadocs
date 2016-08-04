Syntax
------

``` lua
bool getVehicleComponentVisible ( vehicle theVehicle, string theComponent )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") you wish to get component visibility of.
-   **theComponent:** A vehicle component (this is the frame name from the model file of the component you wish to modify)

### Returns

Returns a *bool* indicating the visible state of the component.

Example
-------

**Example 1:** This example would get the name and tells if the component is visible or not.

``` lua
addCommandHandler("icv", -- short for 'is component visible'
    function()
        local theVeh = getPedOccupiedVehicle(localPlayer)
    local getComponent = getVehicleComponents(theVeh) -- returns table with all the components of the vehicle
        if (theVeh) then
            for k in pairs (getComponent) do
            local isVisible = getVehicleComponentVisible(theVeh, k) -- gets if it is visible or not
        if (isVisible == true) then
            outputChatBox(k.." is visible")
        else
            outputChatBox(k.." is not visible")
        end   
            end
        end
    end
)
```

See Also
--------
