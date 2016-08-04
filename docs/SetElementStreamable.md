This function can be used to disable streaming for an element. This will make sure the element is not virtualized (streamed out from GTA) when the player moves far away from it. This function only works in elements with a physical representation in the world (entities), such as [players](/player.md "wikilink"), [peds](/ped.md "wikilink"), [vehicles](/vehicle.md "wikilink") and [objects](/object.md "wikilink").

Syntax
------

``` lua
bool setElementStreamable ( element theElement, bool streamable ) 
```

### Required Arguments

-   **theElement:** The element you wish to set the streaming of
-   **streamable:** *true* if this element should stream in/out like normal, *false* if it should always be streamed in.

### Returns

Returns whether the element could be set to be streamable.

Example
-------

This example creates an [object](/object.md "wikilink") at the center of the map which will always be streamed in when the resource which contains it starts.

``` lua
local function testNonStreamableObjects()
    local object = createObject ( 1097, 0, 0, 5 )
    setElementStreamable ( object, false ) -- Make the object always be streamed in
end
addEventHandler ( "onClientResourceStart", resourceRoot, testNonStreamableObjects )
```

See Also
--------
