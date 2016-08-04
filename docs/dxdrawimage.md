Draws an image on the screen for a single frame. In order for the image to stay visible continuously, you need to call this function with the same parameters on each frame update (see [onClientRender](/docs/onclientrender.md "wikilink")).
Image files should ideally have dimensions that are a power of two, to prevent possible blurring.
<b>Power of two: 2px, 4px, 8px, 16px, 32px, 64px, 128px, 256px, 512px, 1024px...</b>

Syntax
------

``` lua
bool dxDrawImage ( float posX, float posY, float width, float height, mixed image,
                 [ float rotation = 0, float rotationCenterOffsetX = 0, float rotationCenterOffsetY = 0,
                   int color = tocolor(255,255,255,255), bool postGUI = false ] )
```

### Required Arguments

-   **posX:** the absolute X coordinate of the top left corner of the image
-   **posY:** the absolute Y coordinate of the top left corner of the image
-   **width:** the absolute width of the image
-   **height:** the absolute height of the image
-   **image:** Either a [material](/docs/material.md "wikilink") element or a [filepath](/filepath.md "wikilink") of the image which is going to be drawn. (.dds images are also supported). Image files should ideally have dimensions that are a power of two, to prevent possible blurring.

### Optional Arguments

-   **rotation:** the rotation, in degrees for the image.
-   **rotationCenterOffsetX:** the absolute X offset from the image center for which to rotate the image from.
-   **rotationCenterOffsetY:** the absolute Y offset from the image center for which to rotate the image from.
-   **color:** Tints the image with a value produced by [tocolor](/docs/tocolor.md "wikilink") or hexadecimal number in format: 0xAARRGGBB (RR = red, GG = green, BB = blue, AA = alpha).
-   **postGUI:** A bool representing whether the image should be drawn on top of or behind any ingame GUI (rendered by CEGUI).

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

Example of a pendulum swinging from the top of the screen, made using dxDrawImage.

``` lua
local screenWidth,screenHeight = guiGetScreenSize()  -- Get screen resolution.


function renderDisplay ( )
    local seconds = getTickCount() / 1000
    local angle = math.sin(seconds) * 80
    -- This will draw the graphic file 'arrow.png' at the top middle of the screen
    -- using the size of 100 pixels wide, and 240 pixels high.
    -- The center of rotation is at the top of the image.
    dxDrawImage ( screenWidth/2 - 50, 0, 100, 240, 'arrow.png', angle, 0, -120 )
end


function HandleTheRendering ( )
    addEventHandler("onClientRender", root, renderDisplay)  -- Keep everything visible with onClientRender.
end
addEventHandler("onClientResourceStart",resourceRoot, HandleTheRendering)
```

See Also
--------
