This function sets the current blend mode for the dxDraw functions. Changing the blend mode can increase the quality when drawing text or certain other images to a render target. As a general guide use **modulate\_add** when drawing text to a render target, and **add** when drawing the render target to the screen. Don't forget to restore the default **blend** at the end - See the example below.

Syntax
------

``` lua
bool dxSetBlendMode ( string blendMode )
```

### Required Arguments

-   **blendMode :** The blend mode to use which can be one of:
    -   **blend:** The source textures are alpha blended to the screen/render target. This is the default mode for drawing and gives the results we all know and love.
    -   **add:** The source textures are added to the screen/render target.
    -   **modulate\_add:** The source textures are multiplied by the alpha and then added to the screen/render target.
    -   **overwrite :** The source textures are overwritten. This can be useful for clearing render targets.

Returns
-------

Returns true if successful, or *false* if invalid arguments were passed to the function.

Example
-------

This example shows how to use **modulate\_add** and **add** to avoid quality problems when using a render target:

``` lua
local myRenderTarget = dxCreateRenderTarget(500, 500, true)

--
-- Function to draw text to our render target texture when the 'r' key is pressed
--
function updateRenderTarget()
    dxSetRenderTarget(myRenderTarget, true)
    dxSetBlendMode("modulate_add")  -- Set 'modulate_add' when drawing stuff on the render target

    dxDrawText("Testing "..getTickCount(), 0, 0, 0, 0, tocolor(255, 255, 255, 255), 2, "clear")

    dxSetBlendMode("blend")         -- Restore default blending
    dxSetRenderTarget()             -- Restore default render target
end
bindKey("r", "down", updateRenderTarget )

--
-- Display render target contents
--
addEventHandler("onClientRender", root,
    function()
        dxSetBlendMode("add")       -- Set 'add' when drawing the render target on the screen
        dxDrawImage(100, 200, 500, 500, myRenderTarget, -10)
        dxSetBlendMode("blend")     -- Restore default blending
    end
)
```

Requirements
------------

Changelog
---------

See Also
--------
