Syntax
------

``` lua
bool setVehicleComponentVisible ( vehicle theVehicle, string theComponent, bool visible )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") you wish to set component visibility of.
-   **theComponent:** A vehicle component (this is the frame name from the model file of the component you wish to modify)
-   **visible:** a *bool* which determines if the component should be visible

### Returns

Returns a *bool* indicating the visible state of the component.

Example
-------

**Example 1:** This example hide all components when you enter a vehicle.

``` lua
addEventHandler("onClientVehicleEnter", getRootElement(),
    function()
        local getComponent = getVehicleComponents(source) -- get a table with all the components of the vehicle
        for k in pairs (getComponent) do
            setVehicleComponentVisible(source, k, false) -- hides the component
        end
    end
)
```

See Also
--------
