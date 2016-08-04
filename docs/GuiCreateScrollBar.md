This function creates a GUI scrollbar. You can use the functions [guiScrollPaneSetHorizontalScrollPosition](/guiScrollPaneSetHorizontalScrollPosition.md "wikilink"), [guiScrollPaneSetVerticalScrollPosition](/guiScrollPaneSetVerticalScrollPosition.md "wikilink"), [guiScrollPaneGetHorizontalScrollPosition](/guiScrollPaneGetHorizontalScrollPosition.md "wikilink") and [guiScrollPaneGetVerticalScrollPosition](/guiScrollPaneGetVerticalScrollPosition.md "wikilink") to read and modify the scrollbar's scroll.

Syntax
------

``` lua
gui-scrollbar guiCreateScrollBar ( float x, float y, float width, float height, bool horizontal, bool relative, [gui-element parent = nil])
```

### Required Arguments

[frame|Example GUI scrollbar.](/Image:gui-scrollbar.png.md "wikilink")

-   **x:** the 2D x offset of the GUI scrollbar from its parent. This is affected by the *relative* argument.
-   **y:** the 2D y offset of the GUI scrollbar from its parent. This is affected by the *relative* argument.
-   **width:** the width of the GUI scrollbar. This is affected by the *relative* argument.
-   **height:** the height of the GUI scrollbar. This is affected by the *relative* argument.
-   **horizontal:** whether this scrollbar is horizontal (*true*) or vertical (*false*).
-   **relative:** whether sizes and positions are relative to their parent's. If this is *true*, then all measures must be between 0 and 1, representing sizes/positions as a fraction of the parent widget's size.

### Optional Arguments

-   **parent:** the gui-element this scrollbar is attached to. By default, it is nil, meaning the widget is attached to the background.

### Returns

Returns a *gui-scrollbar* if it was created successfully, *false* otherwise.

Example
-------

``` lua
function scBar()
    Window = guiCreateWindow(0.3664,0.2764,0.3508,0.3477,"Window",true)--We create a window.
          guiCreateScrollBar(15,81,24,245,false,false,Window)--We create a scrollbar as a child of 'Window'
end
addEventHandler("onClientResourceStart", resourceRoot, scBar) --We handle it with 'onClientResourceStart' event.
```

See Also
--------
