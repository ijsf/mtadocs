Syntax
------

``` lua
bool dxSetAspectRatioAdjustmentEnabled ( bool bEnabled [, float sourceRatio = 4/3 ] )
```

### Required Arguments

-   **bEnabled**: Should the adjustment be enabled or disabled.

### Optional Arguments

-   **sourceRatio :** This should be set to the aspect ratio the dxDraws were originally designed in.

### Returns

Returns *true* when it was changed successfully, or *false* otherwise.

Requirements
------------

Example
-------

``` lua
scx,scy = guiGetScreenSize()

addEventHandler( "onClientRender", root,
    function()
        dxDrawText( "Hello", 300, 300 )             -- Text will be drawn at 300,300
        dxSetAspectRatioAdjustmentEnabled( true )
        dxDrawText( "Goodbye", 0.78*scx, 0.22*scy )  -- Text will be drawn just below HUD money, with any aspect ratio
    end
)
```

See Also
--------
