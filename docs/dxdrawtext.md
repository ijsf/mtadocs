Draws a string of text on the screen for one frame. In order for the text to stay visible continuously, you need to call this function with the same parameters on each frame update (see [onClientRender](/docs/onclientrender.md "wikilink")).

Syntax
------

``` lua
bool dxDrawText ( string text, float left, float top [, float right=left, float bottom=top, int color=white, float scale=1,
                  mixed font="default", string alignX="left", string alignY="top", bool clip=false, bool wordBreak=false,
                  bool postGUI=false, bool colorCoded=false, bool subPixelPositioning=false,
                  float fRotation=0, float fRotationCenterX=0, float fRotationCenterY=0 ] )
```

### Required Arguments

-   **text:** the text to draw
-   **left:** the absolute X coordinate of the top left corner of the text
-   **top:** the absolute Y coordinate of the top left corner of the text

### Optional Arguments

-   **right:** the absolute X coordinate of the right side of the text bounding box. Used for text aligning, clipping and word breaking.
-   **bottom:** the absolute Y coordinate of the bottom side of the text bounding box. Used for text aligning, clipping and word breaking.
-   **color:** the color of the text, a value produced by [tocolor](/docs/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **scale:** the size of the text.
-   **font:** Either a custom [DX font](/docs/dx_font.md "wikilink") element or the name of a built-in DX font:

-   **alignX:** horizontal alignment of the text within the bounding box. Can be **“left”**, **“center”** or **“right”**.
-   **alignY:** vertical alignment of the text within the bounding box. Can be **“top”**, **“center”** or **“bottom”**.
-   **clip:** if set to *true*, the parts of the text that don't fit within the bounding box will be cut off.
-   **wordBreak:** if set to *true*, the text will wrap to a new line whenever it reaches the right side of the bounding box. If *false*, the text will always be completely on one line.
-   **postGUI:** A bool representing whether the text should be drawn on top of or behind any ingame GUI (rendered by CEGUI).

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

This example code will add the current zone name in the lower left corner of the players' screens.

``` lua
local screenWidth, screenHeight = guiGetScreenSize ( ) -- Get the screen resolution (width and height)


function createText ( )
    local playerX, playerY, playerZ = getElementPosition ( localPlayer )       -- Get our player's coordinates.
    local playerZoneName = getZoneName ( playerX, playerY, playerZ )          -- Get name of the zone the player is in.

    -- Draw zone name text's shadow.
    dxDrawText ( playerZoneName, 44, screenHeight - 41, screenWidth, screenHeight, tocolor ( 0, 0, 0, 255 ), 1.02, "pricedown" )
    -- Draw zone name text.
    dxDrawText ( playerZoneName, 44, screenHeight - 43, screenWidth, screenHeight, tocolor ( 255, 255, 255, 255 ), 1, "pricedown" ) 
end

function HandleTheRendering ( )
    addEventHandler ( "onClientRender", root, createText ) -- keep the text visible with onClientRender.
end

addEventHandler ( "onClientResourceStart", resourceRoot, HandleTheRendering )
```

Changelog
---------

See Also
--------
