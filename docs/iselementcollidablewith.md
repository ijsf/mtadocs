This function can be used to check whether specified element is collidable with another element.
**Note:** You can only use this function with the element types listed below.

-   [Player](/docs/Player.md "wikilink")
-   [Ped](/docs/Ped.md "wikilink")
-   [Vehicle](/docs/Vehicle.md "wikilink")
-   [Object](/docs/Object.md "wikilink")

Syntax
------

``` lua
bool isElementCollidableWith ( element theElement, element withElement ) 
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") which colliding you want to get
-   **withElement:** The other [element](/docs/element.md "wikilink") which colliding with the first entity you want to get

### Returns

Returns *true* if the elements collide with eachother, *false* otherwise.

Example
-------

This example adds the command *togglecol* which toggles the collision between the player and ped.

<section name="Client" class="client" show="true">
``` lua
local tPed = {}
addEventHandler( "onClientPlayerSpawn", localPlayer,
    function()
        local x, y, z = getElementPosition(source)
        if isElement(tPed["thePed"]) then
            destroyElement(tPed["thePed"])
        end
        -- Creates a random ped near player
        tPed["thePed"] = createPed(math.random(209, 238), x+1, y+1, z)
    end
)

function toggleColisionFunc()
    if not isElement(tPed["thePed"]) then
        return
    end
    -- Is the local player collidable with the ped?
    local isCollidable = isElementCollidableWith( localPlayer, tPed["thePed"] )
    -- Toggles the colision with the ped.
    setElementCollidableWith( localPlayer, tPed["thePed"], not isCollidable )
end
-- Adds a command handler to enable/disable colisions with the ped
addCommandHandler("togglecol", toggleColisionFunc)
```

</section>
See Also
--------
