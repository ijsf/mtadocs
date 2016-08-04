This function creates a render target element, which is a special type of [texture](/texture.md "wikilink") that can be drawn on with the dx functions. Successful render target creation is not guaranteed, and may fail due to hardware or memory limitations.

To see if creation is likely to fail, use [dxGetStatus](/dxGetStatus.md "wikilink"). (When **VideoMemoryFreeForMTA** is zero, failure *is* guaranteed.)

Syntax
------

``` lua
element dxCreateRenderTarget ( int width, int height [, bool withAlpha = false ] )
```

### Required Arguments

-   **width :** The width of the texture in pixels.
-   **height :** The height of the texture in pixels.
-   **withAlpha:** The render target will be created with an alpha channel.

### Returns

Returns a [texture](/texture.md "wikilink") element if successful, *false* if the system is unable to create a render target.

**You should always check to see if this function has returned false.**

Example
-------

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
    function()
        myRenderTarget = dxCreateRenderTarget( 80, 100 )            -- Create a render target texture which is 80 x 100 pixels
    end
)

addEventHandler( "onClientRender", root,
    function()
        if myRenderTarget then
            dxSetRenderTarget( myRenderTarget )                     -- Start drawing on myRenderTarget
            dxDrawText ( "Hello", 10, 20 )                          -- Draw a message
            dxSetRenderTarget()                                     -- Stop drawing on myRenderTarget

            dxDrawImage( 50,  50,  100, 100, myRenderTarget )       -- Now use myRenderTarget as a material and draw it lots of times
            dxDrawImage( 150, 350, 150, 100, myRenderTarget )
            dxDrawImage( 250, 250, 100, 150, myRenderTarget )
            dxDrawImage( 350, 30,  150, 150, myRenderTarget )
        end
    end
)
```

See Also
--------
