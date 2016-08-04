Interpolates a 3D Vector between a source value and a target value using either linear interpolation or any other [easing function](/docs/easing.md "wikilink"). It can also be used to interpolate 2D vectors or scalars by only setting some of the x, y, z values and putting 0 to the others.

Syntax
------

``` lua
float float float interpolateBetween ( float x1, float y1, float z1, float x2, float y2, float z2, float fProgress, string strEasingType, [ float fEasingPeriod, float fEasingAmplitude, float fEasingOvershoot ] )
```

### Required Arguments

-   **x1, y1, z1:** 3D coordinates of source vector/value
-   **x2, y2, z2:** 3D coordinates of target vector/value
-   **fProgress:** float between 0 and 1 indicating the interpolation progress (0 at the beginning of the interpolation, 1 at the end).
-   **strEasingType:** the [easing function](/docs/easing.md "wikilink") to use for the interpolation

### Optional Arguments

-   **fEasingPeriod:** the period of the [easing function](/docs/easing.md "wikilink") (only some easing functions use this parameter)
-   **fEasingAmplitude:** the amplitude of the [easing function](/docs/easing.md "wikilink") (only some easing functions use this parameter)
-   **fEasingOvershoot:** the overshoot of the [easing function](/docs/easing.md "wikilink") (only some easing functions use this parameter)

### Returns

Returns *x, y, z* the interpolated 3D vector/value if successful, *false* otherwise (error in parameters). As mentioned before, interpolateBetween can be used on 2D vectors or scalars in which case only some (x, y or just x) of the returned values are to be used (cf. alpha interpolation in marker example or size interpolation in window example).

Examples
--------

The examples below are only clientside examples even though the function can be used on both sides. Indeed it makes more sense to use it with onClientRender/onClientPreRender but the freedom is given to use it in any other context.

<section name="Client" class="client" show="true">
This clientside example uses interpolateBetween to create position and color interpolation(with effect) on a marker. The command to test it is "/marker". The position is interpolated with “OutBounce” as strEasingType to make the marker bounce off the ground and “Linear” interpolation for the color.

``` lua
local g_Marker = nil
addCommandHandler("marker",
function ()
    if g_Marker then return end
    
    local x, y, z = getElementPosition(getLocalPlayer())
    z = z - 1
    
    g_Marker = {}
    g_Marker.startPos = {x, y, z + 5}
    g_Marker.startTime = getTickCount()
    g_Marker.startColor = {255, 0, 0, 0}
    g_Marker.endPos = {x, y, z}
    g_Marker.endTime = g_Marker.startTime + 2000
    g_Marker.endColor = {0, 0, 255, 255}    
    
    local x, y, z = unpack(g_Marker.startPos)
    local r, g, b, a = unpack(g_Marker.startColor)
    g_Marker.marker = createMarker(x, y, z, "cylinder", 1, 255, r, g, b, a)
        
    addEventHandler("onClientRender", getRootElement(), popMarkerUp)
end)

function popMarkerUp()
    local now = getTickCount()
    local elapsedTime = now - g_Marker.startTime
    local duration = g_Marker.endTime - g_Marker.startTime
    local progress = elapsedTime / duration

    local x1, y1, z1 = unpack(g_Marker.startPos)
    local x2, y2, z2 = unpack(g_Marker.endPos)
    local x, y, z = interpolateBetween ( 
        x1, y1, z1,
        x2, y2, z2, 
        progress, "OutBounce")
        
    setElementPosition(g_Marker.marker, x, y, z)
            
    local r1, g1, b1, a1 = unpack(g_Marker.startColor)
    local r2, g2, b2, a2 = unpack(g_Marker.endColor)
    local r, g, b = interpolateBetween ( 
        r1, g1, b1,
        r2, g2, b2, 
        progress, "Linear")
    local a = interpolateBetween ( 
        a1, 0, 0,
        a2, 0, 0,
        progress, "Linear")
        
    setMarkerColor(g_Marker.marker , r, g, b, a)
    
    if now >= g_Marker.endTime then
        removeEventHandler("onClientRender", getRootElement(), popMarkerUp)
        setTimer(
            function ()
                destroyElement(g_Marker.marker)
                g_Marker = nil
            end, 3000, 1)
    end
end
```

</section>
<section name="Client" class="client" show="true">
This clientside example uses interpolateBetween to create size and position interpolation (with effect) on a gui-window. The command to test it is "/window". When the window pops up it uses “OutElastic” as the strEasingType to create the bouncing/elastic effect. When it fades away, it uses “InQuad” to have an accelerating fading.

``` lua
local g_Window = nil
addCommandHandler("window",
function ()
    if g_Window then return end
    
    g_Window = {}
    
    local screenWidth, screenHeight = guiGetScreenSize()
    g_Window.windowWidth, g_Window.windowHeight = 400, 315
    local left = screenWidth/2 - g_Window.windowWidth/2
    local top = screenHeight/2 - g_Window.windowHeight/2
    
    g_Window.window = guiCreateWindow(left, top, g_Window.windowWidth, g_Window.windowHeight, "Interpolation on GUI", false)
    
    g_Window.closeBtn = guiCreateButton(320, 285, 75, 23, "Close", false, g_Window.window)
        
    guiWindowSetSizable(g_Window.window, false)
    guiWindowSetMovable(g_Window.window, false)
    guiSetEnabled(g_Window.window, false)
    guiSetVisible(g_Window.window, false)
    
    g_Window.startTime = getTickCount()
    g_Window.startSize = {0, 0}
    g_Window.endSize = {g_Window.windowWidth, g_Window.windowHeight}
    g_Window.endTime = g_Window.startTime + 1000
    addEventHandler("onClientRender", getRootElement(), popWindowUp)
end)

function on_closeBtn_clicked(button, state, absoluteX, absoluteY)
    if (button ~= "left") or (state ~= "up") then
        return
    end
    
    if not g_Window then return end
    
    showCursor(false)
    guiSetEnabled(g_Window.window, false)
    guiWindowSetMovable(g_Window.window, false)
    
    local screenWidth, screenHeight = guiGetScreenSize()
    local posX, posY = guiGetPosition(g_Window.window, false)
    
    g_Window.startTime = getTickCount()
    g_Window.startSize = {g_Window.windowWidth, g_Window.windowHeight}
    g_Window.startCenter = 
    {
        posX + g_Window.windowWidth/2,
        posY + g_Window.windowHeight/2,
    }
    
    g_Window.endSize = {0, 0}
    g_Window.endTime = g_Window.startTime + 1000
    g_Window.endCenter = 
    {
        screenWidth, 
        screenHeight
    }
    
    addEventHandler("onClientRender", getRootElement(), popWindowDown)
end

function popWindowUp()
    local now = getTickCount()
    local elapsedTime = now - g_Window.startTime
    local duration = g_Window.endTime - g_Window.startTime
    local progress = elapsedTime / duration
        
    local width, height, _ = interpolateBetween ( 
        g_Window.startSize[1], g_Window.startSize[2], 0, 
        g_Window.endSize[1], g_Window.endSize[2], 0, 
        progress, "OutElastic")
        
    guiSetSize(g_Window.window, width, height, false)
    
    local screenWidth, screenHeight = guiGetScreenSize()
    guiSetPosition(g_Window.window, screenWidth/2 - width/2, screenHeight/2 - height/2, false)
    
    if not guiGetVisible(g_Window.window) then
        guiSetVisible(g_Window.window, true)
        guiBringToFront(g_Window.window)
    end
    
    if now >= g_Window.endTime then
        guiSetEnabled(g_Window.window, true)
        
        guiBringToFront(g_Window.window)
        removeEventHandler("onClientRender", getRootElement(), popWindowUp)
        addEventHandler("onClientGUIClick", g_Window.closeBtn, on_closeBtn_clicked, false)
        showCursor(true)
        guiWindowSetMovable(g_Window.window, true)
    end
end

function popWindowDown()
    local now = getTickCount()
    local elapsedTime = now - g_Window.startTime
    local duration = g_Window.endTime - g_Window.startTime
    local progress = elapsedTime / duration
    
    local width, height, _ = interpolateBetween ( 
        g_Window.startSize[1], g_Window.startSize[2], 0, 
        g_Window.endSize[1], g_Window.endSize[2], 0, 
        progress, "InQuad")
        
    guiSetSize(g_Window.window, width, height, false)
    
    local centerX, centerY, _ = interpolateBetween ( 
        g_Window.startCenter[1], g_Window.startCenter[2], 0, 
        g_Window.endCenter[1], g_Window.endCenter[2], 0, 
        progress, "InQuad")
    
    guiSetPosition(g_Window.window, centerX - width/2, centerY - height/2, false)
    
    if now >= g_Window.endTime then
        removeEventHandler("onClientRender", getRootElement(), popWindowDown)
        destroyElement(g_Window.window)
        g_Window = nil
    end
end
```

</section>
<section name="Client" class="client" show="true">
This clientside example uses interpolateBetween to create and position interpolation (with effect) on a camera. The command to test it is "/ccam". When the camera pops up it uses “OutQuad” as the strEasingType to create the slow down effect.

``` lua
local enabled = false
 
addCommandHandler("ccam", function()
    enabled = not enabled
    if enabled then
        start = getTickCount()
        dx, dy, dz, lx, ly, lz = getCameraMatrix()
        addEventHandler("onClientPreRender", root, interpolateCam)
        else
        start = nil
        setCameraTarget(localPlayer)
        removeEventHandler("onClientPreRender", root, interpolateCam)
    end
end)
 
function interpolateCam()
    local now = getTickCount()
    local endTime = start + 2000
    local elapsedTime = now - start
    local duration = endTime - start
    local progress = elapsedTime / duration
    local px, py, pz = getElementPosition(localPlayer)
    local x, y, z = interpolateBetween ( dx, dy, dz, dx+4, dy+4, dz, progress, "OutQuad")
    setCameraMatrix(x, y, z, px, py, pz+0.6, 0, 0)
end
```

</section>
See Also
--------
