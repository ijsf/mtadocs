This function creates a screen source, which is a special type of [texture](/docs/texture.md "wikilink") that contains the screen as rendered by GTA

Note that successful screen source creation is not guaranteed, and may fail due to hardware or memory limitations. You should always check to see if this function has returned false.

Syntax
------

``` lua
element dxCreateScreenSource ( int width, int height )
```

### Required Arguments

-   **width :** The width of the texture in pixels.
-   **height :** The height of the texture in pixels.

### Returns

Returns a [texture](/docs/texture.md "wikilink") [element](/element.md "wikilink") if successful, *false* if invalid arguments were passed to the function.

Example
-------

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
    function()
        myScreenSource = dxCreateScreenSource ( 640, 480 )          -- Create a screen source texture which is 640 x 480 pixels
    end
)

addEventHandler( "onClientRender", root,
    function()
        if myScreenSource then
            dxUpdateScreenSource( myScreenSource )                  -- Capture the current screen output from GTA
            dxDrawImage( 50,  50,  100, 100, myScreenSource )       -- Now use myScreenSource as a material and draw it lots of times
            dxDrawImage( 150, 350, 150, 100, myScreenSource )
            dxDrawImage( 250, 250, 100, 150, myScreenSource )
            dxDrawImage( 350, 30,  150, 150, myScreenSource )
        end
    end
)
```

See Also
--------
