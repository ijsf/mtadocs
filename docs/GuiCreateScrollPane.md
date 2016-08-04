This creates a GUI scroll pane. [frame|Example GUI ScrollPane.](/Image:gui-scrollpane.png.md "wikilink")

Syntax
------

``` lua
element guiCreateScrollPane( float x, float y, float width, float height, bool relative, [gui-element parent = nil])
```

### Required Arguments

-   **x:** the 2D x offset of the GUI scrollpane from its parent. This is affected by the relative argument.
-   **y:** the 2D y offset of the GUI scrollbar from its parent. This is affected by the relative argument.
-   **width:** the width of the GUI scrollpane. This is affected by the relative argument.
-   **height:** the height of the GUI scrollpane. This is affected by the relative argument.
-   **relative:** whether sizes and positions are relative to their parent's. If this is true, then all measures must be between 0 and 1, representing sizes/positions as a fraction of the parent widget's size.

### Optional Arguments

-   **parent:** the gui-element this scrollpane is attached to. By default, it is nil, meaning the widget is attached to the background.

### Returns

The gui-element if created, otherwise false.

Example
-------

This example creates a small window with a scrollpane on. Using the /fill command you can populate the scrollpane with the names of every player in the server.

``` lua
addEventHandler("onClientResourceStart",resourceRoot,
    function()
        -- create a window and create a scrollpane on it
        local window = guiCreateWindow(5,5,130,150,"",false)
        -- the width and height values here are largely irrelevant as the scrollpane will automatically resize when needed
        scrollpane = guiCreateScrollPane(0,0,130,150,false,window)
    end
)

addCommandHandler("fill",
    function()
        -- if the scrollpane exists
        if scrollpane then
            -- delete all the existing labels
            for i,v in ipairs(getElementChildren(scrollpane)) do
                destroyElement(v)
            end
        
            -- for every player in the server
            for i,v in ipairs(getElementsByType("player")) do
                -- create a label with their name on the scrollpane
                guiCreateLabel(5,i*20,90,20,tostring(getPlayerName(v)),false,scrollpane)
            end
        end
    end
)
```

See Also
--------
