<pageclass class="#228B22" subcaption="Useful Function"></pageclass> <lowercasetitle/>

This function calculates the real pixel height of a given font. It does this by drawing and measuring pixels. Therefore it is super accurate (and super slow). Only do this once per font!

Syntax
------

``` lua
float dxGetRealFontHeight( element font )
```

### Required Arguments

-   **font**: Either a custom [DX font](/docs/dx_font.md "wikilink") element or the name of a built-in dx font

### Returns

Returns a float representing the pixel height from the top of the ascenders to the base of the descenders.

Code
----

<section name="Clientside Script" class="client" show="true">
``` lua
function dxGetRealFontHeight(font)
    local cap,base = measureGlyph(font, "S")
    local median,decend = measureGlyph(font, "p")
    local ascend,base2 = measureGlyph(font, "h")

    local ascenderSize = median - ascend
    local capsSize = median - cap
    local xHeight = base - median
    local decenderSize = decend - base

    return math.max(capsSize,ascenderSize) + xHeight + decenderSize
end

function measureGlyph(font, character)
    local rt = dxCreateRenderTarget(128,128)
    dxSetRenderTarget(rt,true)
    dxDrawText(character,0,0,0,0,tocolor(255,255,255),1,font)
    dxSetRenderTarget()
    local pixels = dxGetTexturePixels(rt)
    local first,last = 127,0
    for y=0,127 do
        for x=0,127 do
            local r = dxGetPixelColor( pixels,x,y )
            if r > 0 then
                first = math.min( first, y )
                last = math.max( last, y )
                break
            end
        end
        if last > 0 and y > last+2 then break end
    end
    destroyElement(rt)
    return first,last
end 
```

</section>
Example
-------

<section name="Clientside Script" class="client" show="true">
``` lua
-- TODO
```

</section>
See Also
--------

[Category:Useful Functions](/docs/category-useful_functions.md "wikilink")
