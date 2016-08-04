This function fetches the [pixels](/Texture_pixels.md "wikilink") from a [texture](/texture.md "wikilink") element. It can be used with a standard texture, render target or screen source.

------------------------------------------------------------------------

''Performance note:

-   *This function is slow and not something you want to be doing once a frame.*
-   *It is slower when reading pixels from a render target or screen source.*
-   ''And is very slow indeed if the texture format is not ''' 'argb' ''' ''

------------------------------------------------------------------------

Syntax
------

``` lua
string dxGetTexturePixels ( [ int surfaceIndex = 0, ] element texture [, int x = 0, int y = 0, int width = 0, int height = 0 ] )
```

### Required Arguments

-   **texture :** The texture element to get the pixels from

### Optional Arguments

-   **surfaceIndex:** Desired slice to get if the texture is a volume texture, or desired face to get if the texture is a cube map. (Cube map faces: 0=+X 1=-X 2=+Y 3=-Y 4=+Z 5=-Z)

By default the pixels from the whole texture is returned. To get only a portion of the texture, define a rectangular area using all four of these optional arguments:

-   **x:** Rectangle left position
-   **y:** Rectangle top position
-   **width:** Rectangle width
-   **height :** Rectangle height

Returns
-------

Returns a **'plain**' format pixels string if successful, *false* if invalid arguments were passed to the function.

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
