This function creates a [GUI font](/docs/GUI_font.md "wikilink") element that can be used in [guiSetFont](/guiSetFont.md "wikilink"). Successful font creation is not guaranteed, and may fail due to hardware or memory limitations.

To see if creation is likely to fail, use [dxGetStatus](/docs/dxGetStatus.md "wikilink"). (When **VideoMemoryFreeForMTA** is zero, failure *is* guaranteed.)

##### It is highly recommended that [dxSetTestMode](/docs/dxSetTestMode.md "wikilink") is used when writing and testing scripts using guiCreateFont .

Syntax
------

``` lua
element guiCreateFont ( string filepath[, int size=9 ] )
```

### Required Arguments

-   **filepath:** the name of the file containing the font

### Optional Arguments

-   **size:** size of the font

### Returns

Returns a [GUI font](/docs/GUI_font.md "wikilink") element if successful, *false* if invalid arguments were passed to the function, or there is insufficient resources available.

**You should always check to see if this function has returned false.**

Example
-------

``` lua
-- Display a gui label
local myLabel = guiCreateLabel( 100, 300, 400, 50, "GUI label", false )

-- Use 'toggle' command to switch custom font on and off
addCommandHandler( "toggle",
    function()
        if not myFont then
            myFont = guiCreateFont( "segoeui.ttf", 20 )  -- Create GUI custom font
            guiSetFont( myLabel, myFont )                -- Apply font to a widget
        else        
            destroyElement( myFont )                     -- Destroy custom font
            myFont = nil
        end
    end
)
```

See Also
--------
