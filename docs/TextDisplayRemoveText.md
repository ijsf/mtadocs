This function removes a [textitem](/textitem.md "wikilink") from a [textdisplay](/textdisplay.md "wikilink"). This stops any observers of the [textdisplay](/textdisplay.md "wikilink") from being able to see the [textitem](/textitem.md "wikilink").

Syntax
------

``` lua
void textDisplayRemoveText ( textdisplay displayToRemoveFrom, textitem itemToRemove )
```

### Required Arguments

-   **displayToRemoveFrom**: The [textdisplay](/textdisplay.md "wikilink") to remove the [textitem](/textitem.md "wikilink") from.
-   **itemToRemove**: The [textitem](/textitem.md "wikilink") to remove from the display.

Example
-------

This example creates a text display and adds a “Hello World” text item to it. It then removes that text item 5 seconds later.

``` lua
-- Create a text display.
myTextDisplay = textCreateDisplay ( )
-- Add a player as an observer, i.e. this player will see everything added to this display
textDisplayAddObserver ( myTextDisplay, aPlayer )
-- Create a new text item with the text 'Hello World' and a priority of 'low' and colored red.
myTextItem = textCreateTextItem ( "Hello World", 0.5, 0.5, "low", 255, 0, 0, 0, 1.0 )
-- Add the newly created text item to the display
textDisplayAddText ( myTextDisplay, myTextItem )
-- Remove the text item from the display
setTimer ( textDisplayRemoveText, 5000, 1, myTestDispay, myTextItem )
```

See Also
--------
