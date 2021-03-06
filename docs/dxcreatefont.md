This function creates a [DX font](/docs/dx_font.md "wikilink") element that can be used in [dxDrawText](/docs/dxdrawtext.md "wikilink"). Successful font creation is not guaranteed, and may fail due to hardware or memory limitations.

To see if creation is likely to fail, use [dxGetStatus](/docs/dxgetstatus.md "wikilink"). (When **VideoMemoryFreeForMTA** is zero, failure *is* guaranteed.)

##### It is highly recommended that [dxSetTestMode](/docs/dxsettestmode.md "wikilink") is used when writing and testing scripts using dxCreateFont.

Syntax
------

``` lua
element dxCreateFont ( string filepath[, int size=9, bool bold=false, string quality="proof" ] )
```

### Required Arguments

-   **filepath:** the name of the file containing the font

### Optional Arguments

-   **size:** size of the font
-   **bold:** flag to indicate if the font should be bold
-   **quality:** the font quality
    -   “default”: not the actual default
    -   “draft”
    -   “proof”: the default
    -   “nonantialiased”
    -   “antialiased”
    -   “cleartype”
    -   “cleartype\_natural”

### Returns

Returns a [DX font](/docs/dx_font.md "wikilink") element if successful, *false* if invalid arguments were passed to the function, or there is insufficient resources available.

**You should always check to see if this function has returned false.**

Example
-------

``` lua
local myFont = nil

-- Display text using dxDrawText
addEventHandler( "onClientRender", root,
    function()
        if myFont then
            dxDrawText( "dxDrawText", 100, 350, 300, 350, tocolor(255,255,0), 1, myFont )
        end
    end
)

-- Use 'toggle' command to switch custom font on and off
addCommandHandler( "toggle",
    function()
        if not myFont then
            myFont = dxCreateFont( "segoeui.ttf", 20 )  -- Create custom font
        else        
            destroyElement( myFont )                    -- Destroy custom font
            myFont = nil
        end
    end
)
```

See Also
--------
