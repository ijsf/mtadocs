This function creates a [texture](/texture.md "wikilink") element that can be used in the dxDraw functions.

It is possible to use dxCreateTexture to load cubemaps and volume textures, but these will only be useable as inputs for a shader. The Microsoft utility [DxTex](http://nightly.mtasa.com/files/shaders/DxTex.zip) can view and change cubemaps and volume textures. DxTex can also convert standard textures into DXT1/3/5 compressed .dds which should reduce file sizes.

Syntax
------

``` lua
element dxCreateTexture ( string filepath [, string textureFormat = "argb", bool mipmaps = true, string textureEdge = "wrap" ] )
```

``` lua
element dxCreateTexture ( string pixels [, string textureFormat = "argb", bool mipmaps = true, string textureEdge = "wrap" ] )
```

``` lua
element dxCreateTexture ( int width, int height [, string textureFormat = "argb", string textureEdge = "wrap", string textureType = "2d", int depth = 1 ] )
```

### Required Arguments

-   **filepath:** The filepath of the image. (.bmp, .dds, .jpg, .png, and .tga images are supported). Image files should ideally have dimensions that are a power of two, to prevent possible blurring.

or

-   **pixels:** [Pixels](/Texture_pixels.md "wikilink") containing image data. ('plain', 'jpeg' or 'png' pixels can be used here)

or

-   **width:** Desired width (Must be a power of two. e.g. 128, 256)
-   **height :** Desired height (Must be a power of two. e.g. 128, 256)

### Optional Arguments

-   **textureFormat :** A string representing the desired texture format, which can be one of:
    -   **“argb”** : ARGB uncompressed 32 bit color (default)
    -   **“dxt1”** : DXT1 compressed - Can take a fraction of a second longer to load (unless the file is already a DXT1 .dds). Uses 8 times less video memory than ARGB and can **speed up drawing**. Quality not as good as ARGB and does not support alpha blending.
    -   **“dxt3”** : DXT3 compressed - Can take a fraction of a second longer to load (unless the file is already a DXT3 .dds). Uses 4 times less video memory than ARGB and can **speed up drawing**. Quality slightly better than DXT1 and supports crisp alpha blending.
    -   **“dxt5”** : DXT5 compressed - Can take a fraction of a second longer to load (unless the file is already a DXT5 .dds). Uses 4 times less video memory than ARGB and can **speed up drawing**. Quality slightly better than DXT1 and supports smooth alpha blending.
-   **mipmaps :** True to create a mip-map chain so the texture looks good when drawn at various sizes.
-   **textureEdge :** A string representing the desired texture edge handling, which can be one of:
    -   **“wrap”** : Wrap the texture at the edges (default)
    -   **“clamp”** : Clamp the texture at the edges. This may help avoid edge artifacts.
-   **textureType :** A string representing the desired texture type, which can be one of:
    -   **“2d”** : Standard texture (default)
    -   **“3d”** : Volume texture
    -   **“cube”** : Cube map
-   **depth:** Desired number of slices when creating a volume texture

Returns
-------

Returns a [texture](/texture.md "wikilink") if successful, *false* if invalid arguments were passed to the function.

Example
-------

``` lua
addEventHandler( "onClientRender", root,
    function()
        if myImage then
            dxDrawImage( 100, 350, 300, 350, myImage  )
        end
    end
)

-- Use 'toggle' command to switch image on and off
addCommandHandler( "toggle",
    function()
        if not myImage then
            myImage = dxCreateTexture( "moonpig.png" )  -- Create texture
        else        
            destroyElement( myImage )                 -- Destroy texture
            myImage = nil
        end
    end
)
```

Changelog
---------

See Also
--------
