Syntax
------

``` lua
int int int guiLabelGetColor ( gui-element theLabel )
```

### Required Arguments

-   **theLabel:** The label to get color.

### Returns

Returns three *int* values, representing the amount of red, green, blue if successful. *false* otherwise.

Example
-------

``` lua
local pLabel = guiCreateLabel( 0.5, 0.5, 0.5, 0.5, 'Text', true )
guiLabelSetColor( pLabel, math.random( 0, 255 ), math.random( 0, 255 ), math.random( 0, 255 ) )

addCommandHandler( 'get_color_label', 
    function()
        local iR, iG, iB = guiLabelGetColor( pLabel )
        outputChatBox( ( 'Label color is r = %d, g = %d, b = %d' ):format( iR, iG, iB ) )
    end
)
```

See Also
--------
