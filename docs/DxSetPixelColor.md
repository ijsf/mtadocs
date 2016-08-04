This function sets the color of a single pixel for [pixels](/Texture_pixels.md "wikilink") contained in a string. It only works with **'plain**' format pixels.

Syntax
------

``` lua
bool dxSetPixelColor ( string pixels, int x, int y, int r, int g, int b [, int a = 255 ] )
```

### Required Arguments

-   **pixels :** The pixels to use
-   **x:** The X coordinate for the pixel
-   **y:** The Y coordinate for the pixel
-   **r:** The red channel for the color (0-255)
-   **g:** The green channel for the color (0-255)
-   **b:** The blue channel for the color (0-255)

### Optional Arguments

-   **a:** The alpha channel for the color (0-255)

Returns
-------

Returns true if successful, or *false* if invalid arguments were passed to the function.

Example
-------

<section name="Client" class="client" show="true">
This example creates a 64x64 texture with random pixel colors, and draw it on the screen.

``` lua
addEventHandler ("onClientResourceStart", resourceRoot, 
    function () 
         texture = dxCreateTexture (64, 64)
         local pixels = dxGetTexturePixels (texture)
         for i=0,63 do
             for j=0,63 do
                 dxSetPixelColor (pixels, j, i, math.random (255), math.random (255), math.random (255), 255)
             end;
         end;
         dxSetTexturePixels (texture, pixels)
    end)

addEventHandler ("onClientRender", root,
    function ()
         dxDrawImage (300, 300, 64, 64, texture)
    end)
```

</section>
See Also
--------
