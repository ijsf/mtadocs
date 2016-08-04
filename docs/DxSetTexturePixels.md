This function sets the [pixels](/docs/Texture_pixels.md "wikilink") of a [texture](/texture.md "wikilink") element. It can be used with a standard texture, render target or screen source. Only **'plain**' format pixels please.

------------------------------------------------------------------------

''Performance note:

-   *This function is slow and not something you want to be doing once a frame.*
-   *It is very slow when setting pixels to a render target or screen source.*
-   ''And is very slow indeed if the texture format is not ''' 'argb' ''' ''

------------------------------------------------------------------------

Syntax
------

``` lua
bool dxSetTexturePixels ( [ int surfaceIndex = 0, ] element texture, string pixels [, int x = 0, int y = 0, int width = 0, int height = 0 ] )
```

### Required Arguments

-   **texture :** The texture element to set the pixels of
-   **pixels :** The **'plain**' format pixels to use

### Optional Arguments

-   **surfaceIndex:** Desired slice to set if the texture is a volume texture, or desired face to set if the texture is a cube map. (Cube map faces: 0=+X 1=-X 2=+Y 3=-Y 4=+Z 5=-Z)

By default the pixels are set starting at the top left corner of the texture. To set a different region, define a rectangular area using all four of these optional arguments:

-   **x:** Rectangle left position
-   **y:** Rectangle top position
-   **width:** Rectangle width
-   **height :** Rectangle height

Returns
-------

Returns a string if successful, *false* if invalid arguments were passed to the function.

Example
-------

``` lua
TODO
```

Requirements
------------

Changelog
---------

See Also
--------
