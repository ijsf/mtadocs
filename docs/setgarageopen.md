This function opens or closes the specified garage door in the world.

Syntax
------

``` lua
bool setGarageOpen ( int garageID, bool open )
```

### Required Arguments

-   **garageID:** The [garage ID](/docs/garage.md "wikilink") that represents the garage door being opened or closed.
-   **isOpen:** A boolean indicating whether or not to open the door.

### Returns

Returns *true* if successful, *false* if an invalid garage id was given.

Example
-------

<section name="Server" class="server" show="true">
This example opens a garage door when a player enters a collision shape near it, and closes it when they leave:

``` lua
GARAGE_ID = 25

-- create a collision shape and attach event handlers to it when the resource starts
addEventHandler("onResourceStart", getResourceRootElement(),
function (resource)
    local garageCube = createColCuboid(1337, 194, 28, 6, 10, 4)
    addEventHandler("onColShapeHit", garageCube, onGarageCubeHit)
    addEventHandler("onColShapeLeave", garageCube, onGarageCubeLeave)
end)

-- open the door when someone enters the garage's collision shape
function onGarageCubeHit(hitElement, matchingDimension)
    if (getElementType(hitElement) == "player") then
        -- check to make sure the door is closed
        if (not isGarageOpen(GARAGE_ID)) then
            -- open the door
            setGarageOpen(GARAGE_ID, true)
        end
    end
end

-- close the door when someone leaves the garage's collision shape
function onGarageCubeLeave(leaveElement, matchingDimension)
    if (getElementType(leaveElement) == "player") then
        -- check to make sure the door is open
        if (isGarageOpen(GARAGE_ID)) then
            -- close the door
            setGarageOpen(GARAGE_ID, false)
        end
    end
end
```

</section>
See Also
--------

[ru:setGarageOpen](/docs/ru:setgarageopen.md "wikilink")
