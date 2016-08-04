This function creates a text item. A text item represents a single area of text, much like a label does in standard GUI programming. A text item can only be seen by players if it is added to a [textdisplay](/textdisplay.md "wikilink") using [textDisplayAddText](/textDisplayAddText.md "wikilink"). Each text item can be added to multiple displays, if need be.

Syntax
------

``` lua
 textitem textCreateTextItem ( string text, float x, float y, [string priority, int red = 255, int green = 255, int blue = 255, int alpha = 255, float scale = 1, string alignX = "left", string alignY = "top", int shadowAlpha = 0] )
```

### Required Arguments

-   **text**: A string of text you want to display
-   **x**: A floating point number between 0.0 and 1.0 indicating how far across the screen the text should be shown, as a percentage of the width, from the left hand side.
-   **y**: A floating point number between 0.0 and 1.0 indicating how far down the screen the text should be shown, as a percentage of the height, from the top.

### Optional Arguments

-   **priority**: How important it is that this text should be up to date on client's screens. Valid values are: “low”, “medium”, “high” which are aliases for 0, 1 and 2 respectively.
-   **red**: A value between 0 and 255 indicating how red the text should be.
-   **green**: A value between 0 and 255 indicating how green the text should be.
-   **blue**: A value between 0 and 255 indicating how blue the text should be.
-   **alpha**: A value between 0 and 255 indicating how transparent the text should be, with 0 being fully transparent, and 255 being opaque.
-   **scale**: A floating point value indicating the scale of the text. The default is 1.0, which is around 12pt.
-   **alignX**: A string representing the X-alignment of the text. (“left”, “center”, “right”)
-   **alignY**: A string representing the Y-alignment of the text. (“top”, “center”, “bottom”)
-   **shadowAlpha**: A value between 0 and 255 indicating how dark the drop shadow should be.

### Returns

Returns a [textitem](/textitem.md "wikilink") object.

Example
-------

``` lua
myDisplay = textCreateDisplay ()                              -- create a display
textDisplayAddObserver ( myDisplay, myPlayer )                -- make it visible to a player
myTextItem = textCreateTextItem ( "Hello world!", 0.5, 0.5 )  -- create text item for the display
textDisplayAddText ( myDisplay, myTextItem )                  -- add created item to text display so it is displayed
```

See Also
--------

[ru:textCreateTextItem](/ru:textCreateTextItem.md "wikilink")
