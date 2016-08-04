This function set component rotation for [vehicle](/docs/vehicle.md "wikilink").

Syntax
------

``` lua
bool setVehicleComponentRotation ( vehicle theVehicle, string theComponent, float rotX, float rotY, float rotZ [, string base = "parent"] )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") you wish to set component rotation.
-   **theComponent:** A vehicle component (this is the frame name from the model file of the component you wish to modify)
-   **rotX:** The component's rotation around the x axis in degrees.
-   **rotY:** The component's rotation around the y axis in degrees.
-   **rotZ:** The component's rotation around the z axis in degrees.

### Optional Arguments

### Returns

Return *true* if component rotation was set successfully, *false* otherwise.

Example
-------

**Example 1:** This example would change the roatation of the component when the player enters a vehicle.

``` lua
addEventHandler("onClientVehicleEnter", getRootElement(),
    function()
        local theVeh = getPedOccupiedVehicle(localPlayer)
        local getComponent = getVehicleComponents(theVeh) -- returns table with all the components of the vehicle
        if (theVeh) then
        for k in pairs (getComponent) do
            local rx, ry, rz = getVehicleComponentRotation(theVeh, k) --get the rotation of the component
                setVehicleComponentRotation(theVeh, k, rx+10, ry+10, rz+10) -- increases by 10 unit
        end
        end
    end
)
```

Changelog
---------

See Also
--------
