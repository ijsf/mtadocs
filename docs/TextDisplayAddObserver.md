This function adds a [player](/player.md "wikilink") as an observer of a [textdisplay](/textdisplay.md "wikilink"). This allows the [player](/player.md "wikilink") to see any [textitems](/textitem.md "wikilink") that the [textdisplay](/textdisplay.md "wikilink") contains.

Syntax
------

``` lua
void textDisplayAddObserver ( textdisplay display, player playerToAdd )
```

### Required Arguments

-   **display**: The [textdisplay](/textdisplay.md "wikilink") to add the [player](/player.md "wikilink") to as an observer.
-   **playerToAdd**: The [player](/player.md "wikilink") that should observe the [textdisplay](/textdisplay.md "wikilink").

Example
-------

``` lua
function MyTestTextFunction ()
display = textCreateDisplay ()                 -- create a new display, store the reference in a variable called display
textDisplayAddObserver ( display, thePlayer )  -- add an observer to it
text = textCreateTextItem ( "Hello World", 0.5, 0.5, "medium", 255, 0, 0, 255, 2, "left", "top", 255) --red text of 24pt at the center of your screen
textDisplayAddText ( display, text )           -- Add the text item to the text display
end
```

See Also
--------
