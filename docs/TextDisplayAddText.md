This function adds a [textitem](/docs/textitem.md "wikilink") to a [textdisplay](/textdisplay.md "wikilink"). This allows any observers of the [textdisplay](/textdisplay.md "wikilink") to see the [textitem](/textitem.md "wikilink").

Syntax
------

``` lua
void textDisplayAddText ( textdisplay displayToAddTo, textitem itemToAdd )
```

### Required Arguments

-   **displayToAddTo**: The [textdisplay](/docs/textdisplay.md "wikilink") to add the [textitem](/textitem.md "wikilink") to.
-   **itemToAdd**: The [textitem](/docs/textitem.md "wikilink") to add to the display.

Example
-------

``` lua
-- Create a text display.
myTextDisplay = textCreateDisplay ()
-- Add a player as an observer, i.e. this player will see all text items that are on this display
textDisplayAddObserver ( myTextDisplay, aPlayer )
-- Create a new text item with the text 'Hello World' and a priority of 'low' and colored red.
myTextItem = textCreateTextItem ( "Hello World", 0.5, 0.5, "low", 255, 0, 0, 0, 1.0 )
-- Add the newly created text item to the display
textDisplayAddText ( myTextDisplay, myTextItem )
```

See Also
--------
