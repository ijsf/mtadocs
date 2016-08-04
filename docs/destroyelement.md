This function destroys an [element](/docs/element.md "wikilink") and all elements within it in the hierarchy (its children, the children of those children etc). [Player](/player.md "wikilink") elements cannot be destroyed using this function. A player can only be removed from the hierarchy when they quit or are kicked. The root element also cannot be destroyed, however, passing the root as an argument will wipe all elements from the server, except for the players and clients, which will become direct descendants of the root node, and other elements that cannot be destroyed, such as resource root elements.

Players are not the only elements that cannot be deleted. This list also includes remote clients and console elements.

Syntax
------

``` lua
bool destroyElement ( element elementToDestroy )
```

### Required Arguments

-   **elementToDestroy:** The element you wish to destroy.

### Returns

Returns *true* if the element was destroyed successfully, *false* if either the element passed to it was invalid or it could not be destroyed for some other reason (for example, clientside destroyElement can't destroy serverside elements).

Example
-------

**Example 1:** This example would destroy every element in the map, with the exception of players and the root element itself.

``` lua
-- Destroy all its children, except players.
destroyElement ( root )
```

**Example 2:** This example destroys all vehicles of the specified model:

``` lua
function destroyVehiclesOfModel(modelID)
    -- get a table of all the vehicles that exist and loop through it
    local vehicles = getElementsByType("vehicle")
    for i,v in ipairs(vehicles) do
        -- if the vehicle's ID is the one provided, destroy it
        if (getElementModel(v) == modelID) then
            destroyElement(v)
        end
    end
end

destroyVehiclesOfModel(445)
```

**Example 3:** This example allows creation of claymores, which trigger and explode. When they explode, the colshape and object for the claymore are destroyed.

``` lua
function createClaymore ( x,y,z, creator )
    local claymoreObject = createObject ( 1945, x, y, z - 1, 0, 0, 90 )  -- create an object which looks like a claymore
    local claymoreCol = createColSphere ( x, y, z, 1 )                   -- create a col sphere with radius 1
    setElementData ( claymoreCol, "object", claymoreObject )             -- store the object of the claymore
    setElementData ( claymoreCol, "creatorPlayer", creator )             -- store the person who created it
    addEventHandler ( "onColShapeHit", claymoreCol, claymoreHit )        -- add an event handler to the colshape
end

function claymoreHit ( thePlayer, matchingDimension )
    -- retrieve the object associated to the claymore, and who created it
    local claymoreObject = getElementData ( source, "object" )
    local claymoreCreator = getElementData ( source, "creatorPlayer" )
    -- get the position of the claymore
    local x,y,z = getElementPosition ( source )
    createExplosion ( x,y,z, 12, claymoreCreator ) -- create an explosion, associated to the creator, of a small size at the col's position
    -- remove the event handler for the colshape
    removeEventHandler ( "onColShapeHit", source, claymoreHit )
    -- destroy the claymore object, and the col shape so it doesn't trigger again.
    destroyElement ( claymoreObject )
    destroyElement ( source )
end
```

**Example 4:** This example destroys all vehicles, regardless of ID, name, etc:

``` lua
function allvehiclesaredoomed()
    -- get a table of all the vehicles that exist and loop through it
    vehicles = getElementsByType("vehicle")
    for i,v in ipairs(vehicles) do
        -- destroy every vehicle.
        destroyElement(v)
    end
end
--The command handler below will destroy all vehicles once
--you enter /vdoom in the chat box or vdoom in the game console.
addCommandHandler("vdoom", allvehiclesaredoomed)
--This is very useful if you use the freeroam resource and some
--heartless players start spawn spamming.
--You can also set it on a timer to have your server clear all
--vehicles ever 60 minutes, (1 hour).  Timer below:
setTimer(allvehiclesaredoomed, 3600000, 0)
```

See Also
--------
