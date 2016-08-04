Syntax
------

``` lua
 )
```

### Required Arguments

-   **lightType:** An integer representing the type of light to create.

-   **posX:** A floating point number representing the X coordinate on the map.
-   **posY:** A floating point number representing the Y coordinate on the map.
-   **posZ:** A floating point number representing the Z coordinate on the map.

### Optional Arguments

-   **radius:** A floating point number representing the radius of the light.
-   **r:** An integer number representing the amount of red to use in the colouring of the light (0 - 255).
-   **g:** An integer number representing the amount of green to use in the colouring of the light (0 - 255).
-   **b:** An integer number representing the amount of blue to use in the colouring of the light (0 - 255).
-   **dirX:** A floating point number representing the light direction's X coordinate on the map.
-   **dirY:** A floating point number representing the light direction's Y coordinate on the map.
-   **dirZ:** A floating point number representing the light direction's Z coordinate on the map.
-   **createsShadow:** A boolean representing whether or not does the light cast shadows.

### Returns

Returns the [light](/docs/Element/Light.md "wikilink") element if creation was successful, *false* otherwise.

Example
-------

This example will make every player to look completely black without using shaders. It will also dark vehicles he uses too.

``` lua
local lightRadius = 2 * getElementRadius(localPlayer) -- Every standard player model has the same radius, so save it for quicker access
local lights = { [localPlayer] = createLight(2, 0, 0, 0, lightRadius) } -- Initialize our light table with the one that the local player will use for the effect

local function addPlayerDarkLight()
    -- Create a new dark light for that player
    lights[source] = createLight(2, 0, 0, 0, lightRadius)
end
addEventHandler("onClientPlayerJoin", root, addPlayerDarkLight)

local function removePlayerDarkLight()
    -- Destroy the light of that player and remove references
    destroyElement(lights[source])
    lights[source] = nil
end
addEventHandler("onClientPlayerQuit", root, removePlayerDarkLight)

-- Make the dark light assigned to each player to move with his center, so we achieve the desired effect
local function updateLightPositions()
    for player, light in pairs(lights) do
        setElementPosition(light, getPedBonePosition(player, 2))
    end
end
addEventHandler("onClientPreRender", root, updateLightPositions)
```

Changelog
---------

See Also
--------
