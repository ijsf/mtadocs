Syntax
------

``` lua
table getVehicleComponents ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") you wish to get the components of.

### Returns

Returns a *table* containing the name of the component as the key and visibility flag of that component as the value

Example
-------

<section name="Client" class="client" show="true">
``` lua
addCommandHandler ( "gvc",
    function ( )
        local theVehicle = getPedOccupiedVehicle ( localPlayer )
        if ( theVehicle ) then
            for k in pairs ( getVehicleComponents ( theVehicle ) ) do
                outputChatBox ( k )
            end
        end
    end
)
```

</section>
<section name="Client" class="client" show="true">
This example draw all components names on the player screen.

``` lua
addEventHandler ( "onClientRender", root,
function()
    if isPedInVehicle ( localPlayer ) and getPedOccupiedVehicle ( localPlayer ) then
        local veh = getPedOccupiedVehicle ( localPlayer )
        for v in pairs ( getVehicleComponents(veh) ) do
            local x,y,z = getVehicleComponentPosition ( veh, v, "world" )
            local wx,wy,wz = getScreenFromWorldPosition ( x, y, z )
            if wx and wy then
                dxDrawText ( v, wx -1, wy -1, 0 -1, 0 -1, tocolor(0,0,0), 1, "default-bold" )
                dxDrawText ( v, wx +1, wy -1, 0 +1, 0 -1, tocolor(0,0,0), 1, "default-bold" )
                dxDrawText ( v, wx -1, wy +1, 0 -1, 0 +1, tocolor(0,0,0), 1, "default-bold" )
                dxDrawText ( v, wx +1, wy +1, 0 +1, 0 +1, tocolor(0,0,0), 1, "default-bold" )
                dxDrawText ( v, wx, wy, 0, 0, tocolor(0,255,255), 1, "default-bold" )
            end
        end
    end
end)
```

by **FusioN**.

</section>
See Also
--------
