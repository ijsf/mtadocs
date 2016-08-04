This function changes the drawing destination for the dx functions. It can be used to select a previously created render target, or if called with no arguments, restore drawing directly to the screen.

Syntax
------

``` lua
bool dxSetRenderTarget ( [ element renderTarget, bool clear = false ] )
```

If no arguments are supplied, the screen is restored as the drawing destination.

### Optional Arguments

-   **renderTarget:** The render target element whose pixels we want to draw on.
-   **clear:** If set to true, the render target will also be cleared.

### Returns

Returns *true* if the render target was successfully changed, *false* otherwise.

Usage restrictions
------------------

-   Items drawn with *postGUI* set to *true* will not appear on a custom render target.

Example
-------

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
    function()
        myRenderTarget = dxCreateRenderTarget( 80, 100 )  -- Create a render target texture which is 80 x 100 pixels
    end
)

addEventHandler( "onClientRender", root,
    function()
        if myRenderTarget then
            dxSetRenderTarget( myRenderTarget )  -- Select custom render target
            dxDrawText ( "Hello", 10, 20 )       -- The message 'Hello' will be drawn on myRenderTarget

            dxSetRenderTarget()                  -- Select default render target
            dxDrawText ( "Goodbye", 10, 20 )     -- The message 'Goodbye' will be drawn directly to the screen
        end
    end
)
```

This example shows how you can prepare render target contents at anytime (from client version 1.3.0-9.04431)

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
    function()
        myRenderTarget = dxCreateRenderTarget( 80, 100 )     -- Create a render target texture which is 80 x 100 pixels
        dxSetRenderTarget( myRenderTarget )                  -- Select custom render target for drawing
        dxDrawRectangle ( 2, 2, 60, 60, tocolor(255,255,0) ) -- Draw anything you like (to the render target)
        dxDrawText ( "Hello", 10, 20 )
        dxDrawText ( "This is", 10, 40 )
        dxDrawText ( "Amazing", 10, 60 )
        dxSetRenderTarget()                                  -- Unselect custom render target
    end
)

addEventHandler( "onClientRender", root,
    function()
        if myRenderTarget then
            dxDrawImage ( 100, 200, 80, 100, myRenderTarget )        -- Draw myRenderTarget content to the screen
        end
    end
)
```

Changelog
---------

See Also
--------
