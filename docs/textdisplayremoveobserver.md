This function removes a [player](/docs/player.md "wikilink") observer of a [textdisplay](/textdisplay.md "wikilink"). This stops the [player](/player.md "wikilink") from being able to see [textitems](/textitem.md "wikilink") that the [textdisplay](/textdisplay.md "wikilink") contains.

Syntax
------

``` lua
bool textDisplayRemoveObserver ( textdisplay display, player playerToRemove )
```

### Required Arguments

-   **display**: The [textdisplay](/docs/textdisplay.md "wikilink") to remove the [player](/player.md "wikilink") from as an observer.
-   **playerToRemove**: The [player](/docs/player.md "wikilink") that should be removed from the [textdisplay](/textdisplay.md "wikilink").

Example
-------

This example creates a new display and a “Hello World” text item for a player. It then removes it from his screen 5 seconds later

``` lua
display = textCreateDisplay ( ) --create the display
textDisplayAddObserver ( display, thePlayer ) --add an observer
newtextitem = textCreateTextItem ( "Hello World", 0.5, 0.5, "low", 255, 0, 0, 0, 1.0 ) --create our "Hello World" text item
textDisplayAddText ( display, newtextitem ) --add this to the display
setTimer ( textDisplayRemoveObserver, 5000,1, display, thePlayer ) --set a timer to remove this 5 seconds later.
```

See Also
--------
