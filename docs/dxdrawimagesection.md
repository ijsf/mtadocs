Differing from [dxDrawImage](/docs/dxdrawimage.md "wikilink"), this function only draws a part of an image on the screen for a single frame. In order for the image to stay visible continuously, you need to call this function with the same parameters on each frame update (see [onClientRender](/docs/onclientrender.md "wikilink")).

Syntax
------

``` lua
bool dxDrawImageSection ( float posX, float posY, float width, float height,
                          float u, float v, float usize, float vsize, mixed image,
                        [ float rotation = 0, float rotationCenterOffsetX = 0, float rotationCenterOffsetY = 0,
                          int color = white, bool postGUI = false ] )
```

### Required Arguments

-   **posX:** the absolute X coordinate of the top left corner of the image
-   **posY:** the absolute Y coordinate of the top left corner of the image
-   **width:** the absolute width of the image
-   **height:** the absolute height of the image
-   **u:** the absolute X coordinate of the top left corner of the section which should be drawn from image
-   **v:** the absolute Y coordinate of the top left corner of the section which should be drawn from image
-   **usize:** the absolute width of the image section
-   **vsize:** the absolute height of the image section
-   **image:** Either a [material](/docs/material.md "wikilink") element or a [filepath](/docs/filepath.md "wikilink") of the image which is going to be drawn. (.dds images are also supported). Image files should ideally have dimensions that are a power of two, to prevent possible blurring.

### Optional Arguments

-   **rotation:** the rotation, in degrees for the image.
-   **rotationCenterOffsetX:** the absolute X offset from the image center for which to rotate the image from.
-   **rotationCenterOffsetY:** the absolute Y offset from the image center for which to rotate the image from.
-   **color:** the color of the image, a value produced by [tocolor](/docs/tocolor.md "wikilink") or hexadecimal number in format: 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **postgui :** A bool representing whether the image should be drawn on top of or behind any ingame GUI (rendered by CEGUI).

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

The example draws a section of an image. (You can use [this](http://i1325.photobucket.com/albums/u630/Tourmalinelisa2/128x128.jpg) image to test.)

``` lua
addEventHandler('onClientRender', root, function()
  dxDrawImageSection(400, 200, 64, 64, 0, 0, 64, 64, 'img.jpg') -- Draw a certain section
  dxDrawImage(400, 300, 128, 128, 'img.jpg') -- Draw the whole image to be able to identify the difference
end)
```

See Also
--------
