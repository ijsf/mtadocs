<pageclass class="#228B22" subcaption="Useful Function"></pageclass> <lowercasetitle/>

This function calculate a font size from given height for dxDraw.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **height**: The font height in pixels.

### Optional Arguments

-   **font**: Either a custom [DX font](/DX_font.md "wikilink") element or the name of a built-in dx font:

### Returns

Returns an float of the font size.

Code
----

<section name="Clientside Script" class="client" show="true">
``` lua
function dxGetFontSizeFromHeight( height, font )
    if type( height ) ~= "number" then return false end
    font = font or "default"
    local ch = dxGetFontHeight( 1, font )
    return height/ch
end 
```

</section>
Example
-------

<section name="Clientside Script" class="client" show="true">
``` lua
function render()
    local size = dxGetFontSizeFromHeight( 250, "pricedown" )
    dxDrawText( "Hello World", 500, 500, 1000, 1000, tocolor(255,128,0,255), size, "pricedown" )
end

addEventHandler( "onClientRender", getRootElement(), render )
```

</section>
Author: bartekPL

See Also
--------

[Category:Useful Functions](/Category:Useful_Functions.md "wikilink")
