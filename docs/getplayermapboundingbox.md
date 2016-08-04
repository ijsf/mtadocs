This function gets the GUI bounding box of the radar map texture.

Syntax
------

``` lua
int, int, int, int getPlayerMapBoundingBox ()
```

### Returns

-   If the player's map is showing, it returns four integers: *minX*, *minY*, *maxX*, *maxY*. These are **absolute** position coordinates of where the player's map is drawn on the screen.
    -   *minX, minY* represent the world coordinates *-3000, 3000* (upper-left corner of the world map).
    -   *maxX, maxY* represent the world coordinates *3000, -3000* (lower-right corner of the world map).
    -   Negative values may be returned if these coordinates are off screen.
-   If the map is not showing, a *false* boolean value is returned.

Examples
--------

This example draws the text “Center of SA map” in the F11 map screen where the center of world coordinates is.

``` lua
local worldPos = Vector2(0, 0) -- Center of coordinates, which is somewhere in Blueberry Acres
local screenSize = Vector2(guiGetScreenSize())

local function drawWorldPosMapText()
    local mapMin, mapMax
    do
        -- We do these operations inside a block to delete intermediate variables automatically
        local mx, my, Mx, My = getPlayerMapBoundingBox()
        if mx then
            mapMin = Vector2(mx, my)
            mapMax = Vector2(Mx, My)
        else
            -- Do not continue if the screen coordinates could not be calculated (i.e. map is not showing)
            return
        end
    end

    -- Calculate a factor in range [0, 1] which represents the relative distance to the max world coords point from the min world coords point of the given coordinates (worldPos)
    -- 0 means that the given point is in mapMin in a certain direction
    -- 1 means that the given point is in mapMax in a certain direction
    -- Assumes the world map is a square whose side is 6000 units long
    local fMx, fMy = (worldPos.x + 3000) / 6000, -(worldPos.y - 3000) / 6000
    -- Do the opposite thing for the min coords point
    local fmx, fmy = 1 - fMx, 1 - fMy

    -- Use the factors and given screen points to calculate the final screen coords of our world position in the map
    local screenMapPos = Vector2((fmx * mapMin.x) + (fMx * mapMax.x), (fmy * mapMin.y) + (fMy * mapMax.y))

    -- Check whether our screen position is within the viewable screen area (this is not necessary when working with dxDrawText anyway)
    if screenMapPos.x >= 0 and screenMapPos.y >= 0 and screenMapPos.x <= screenSize.x and screenMapPos.y <= screenSize.y then
        -- Finally, draw our desired text
        local width = dxGetTextWidth("Center of SA map")
        dxDrawText("Center of SA map", screenMapPos.x - (width / 2), screenMapPos.y, screenMapPos.x + (width / 2), screenMapPos.y, tocolor(255, 255, 0), 1, "default", "center", "center")
    end
end
addEventHandler("onClientRender", root, drawWorldPosMapText)
```

This example lets players set a target blip in their radar by clicking with the left mouse button in the desired place in the F11 world map, and delete it by clicking with the right mouse button.

``` lua
local targetBlipIcon = 41 -- The target blip icon to use. Defaults to the Waypoint icon

local screenSize = Vector2(guiGetScreenSize())
local wasLeftMouseButtonPressed, wasRightMouseButtonPressed, targetBlip = false, false

local function handleMapTargetBlip()
    -- Do nothing if the map is not showing but reset our state variables and mouse
    if not isPlayerMapVisible() then
        showCursor(false, false)
        wasLeftMouseButtonPressed, wasRightMouseButtonPressed = false, false
        return
    end

    -- If the cursor is not showing, show it, so the player can click on the desired target point
    if not isCursorShowing() then
        showCursor(true, false)
    end

    -- If we have just started to click the left mouse button, do the actual target blip creation
    local isLeftMouseButtonPressed = getKeyState("mouse1")
    if isLeftMouseButtonPressed and isLeftMouseButtonPressed ~= wasLeftMouseButtonPressed then
        -- Get the cursor and map bounding box positions
        local cursorPos, mapMin, mapMax = Vector2(getCursorPosition())

        -- Transform the relative cursor position to absolute position
        cursorPos.x, cursorPos.y = cursorPos.x * screenSize.x, cursorPos.y * screenSize.y

        -- Calculate our map points vectors inside a block to delete intermediate variables automatically
        do
            local mx, my, Mx, My = getPlayerMapBoundingBox()
            mapMin = Vector2(mx, my)
            mapMax = Vector2(Mx, My)
        end

        -- If the cursor is inside the map rectangle, create or update the target blip
        -- Otherwise, just ignore the click
        if cursorPos.x >= mapMin.x and cursorPos.y >= mapMin.y and cursorPos.x <= mapMax.x and cursorPos.y <= mapMax.y then
            -- Get the relative position (in range [0, 1]) of the mouse click point from the mapMin point
            -- 0 in a direction means that the cursor is in mapMin in that direction
            -- 1 in a direction means that the cursor is in mapMax in that direction
            local relPos = Vector2((cursorPos.x - mapMin.x) / (mapMax.x - mapMin.x), (cursorPos.y - mapMin.y) / (mapMax.y - mapMin.y))

            -- Translate that relative position to 2D world coordinates
            -- Assumes the world map is a square whose side is 6000 units long
            local worldPlanePos = Vector2(6000 * (relPos.x - 0.5), 3000 - (relPos.y * 6000))

            -- Get a 3D world position by adding the highest ground Z coordinate, which is what we usually want
            -- Note that only the blip ID 0 (marker) uses this additional coordinate. For the rest of blips, we could pass a dummy value instead
            local worldPos = Vector3(worldPlanePos.x, worldPlanePos.y, getGroundPosition(worldPlanePos.x, worldPlanePos.y, 3000))

            -- If we don't have a target blip, create it. Otherwise, just update its position
            if not targetBlip then
                targetBlip = createBlip(worldPos, targetBlipIcon)
            else
                setElementPosition(targetBlip, worldPos)
            end
        end
    end

    -- If we have a target blip, destroy it and its variable if we have just started to click the right mouse button
    local isRightMouseButtonPressed = getKeyState("mouse2")
    if targetBlip then
        if isRightMouseButtonPressed and isRightMouseButtonPressed ~= wasRightMouseButtonPressed then
            destroyElement(targetBlip)
            targetBlip = nil
        end
    end

    -- Save the mouse button states for future checks
    wasLeftMouseButtonPressed, wasRightMouseButtonPressed = isLeftMouseButtonPressed, isRightMouseButtonPressed
end
addEventHandler("onClientRender", root, handleMapTargetBlip)
```

See also
--------
