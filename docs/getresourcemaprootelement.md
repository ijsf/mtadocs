This function retrieves the root element of a certain [map](/docs/map.md "wikilink") in a specified [resource](/resource.md "wikilink").

Syntax
------

``` lua
element getResourceMapRootElement ( resource theResource, string mapName )
```

### Required Arguments

-   **theResource:** the resource where the map is located
-   **mapName:** name of the maps which root element we want to retrieve, file extension is required

### Returns

Returns an the resource's map root [element](/docs/element.md "wikilink") if the map exists and resource specified was valid and active (currently running), *false* otherwise.

Example
-------

This example shows how to get all elements of specific type only from one map.

``` lua
-- We have 2 map files in our meta.xml: island_1.map, island_2.map.
-- These maps contains objects, vehicles, pickups, etc.
-- After resource start we must found all vehicles only from island_1.map and lock them.

-- `resourceRoot` is predefined script variable containing current resource root pointer
addEventHandler( 'onResourceStart', resourceRoot,
    function()
        -- `resource` is predefined script variable containing current resource pointer
        local island_1_mapRoot = getResourceMapRootElement( resource, 'island_1.map' )
        local island_1_vehicles = getElementsByType( 'vehicle', island_1_mapRoot )
        
        for vehicle in ipairs(island_1_vehicles) do
            setVehicleLocked( vehicle, true )
        end
    end
)
```

See Also
--------
