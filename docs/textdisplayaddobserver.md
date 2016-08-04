This function adds a [player](/docs/player.md "wikilink") as an observer of a [textdisplay](/docs/textdisplay.md "wikilink"). This allows the [player](/docs/player.md "wikilink") to see any [textitems](/docs/textitem.md "wikilink") that the [textdisplay](/docs/textdisplay.md "wikilink") contains.

Syntax
------

``` lua
void textDisplayAddObserver ( textdisplay display, player playerToAdd )
```

### Required Arguments

-   **display**: The [textdisplay](/docs/textdisplay.md "wikilink") to add the [player](/docs/player.md "wikilink") to as an observer.
-   **playerToAdd**: The [player](/docs/player.md "wikilink") that should observe the [textdisplay](/docs/textdisplay.md "wikilink").

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
