Gets the specified vehicle's current gear.

Syntax
------

``` lua
int getVehicleCurrentGear ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** the vehicle to get the gear of

### Returns

Returns the gear if successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
Example of a program that outputs the current gear to the lower, center of the screen

``` lua

g_player = getLocalPlayer()
g_root = getRootElement()

function makeGearGui( )
    local sx,sy = guiGetScreenSize()
    local wx = 50
    local wy = 50
    gearLabel = guiCreateLabel(((sx/2)-wx),(sy-wy),wx,wy,"5",false)
end

function onRender()
    g_vehicle = getPedOccupiedVehicle(g_player)
    if g_vehicle then
        g_curGear = tostring(getVehicleCurrentGear(g_vehicle))
        guiSetText(gearLabel,g_curGear)
    else
        guiSetText(gearLabel,"")
    end
end

makeGearGui()
addEventHandler("onClientRender",g_root,onRender)
```

</section>
See Also
--------
