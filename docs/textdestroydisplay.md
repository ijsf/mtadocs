This function destroys a text display and will unlink all the [textitems](/docs/textitem.md "wikilink") on it. This does not stop the textitems existing, but anyone who was observing the textitems through this display will stop seeing them.

Syntax
------

``` lua
bool textDestroyDisplay ( textdisplay display )
```

### Required Arguments

-   **display:** This is the [textdisplay](/docs/textdisplay.md "wikilink") that you wish to have destroyed.

Example
-------

This example creates a display then destroys it again straight away.

``` lua
myDisplay = textCreateDisplay ()
textDestroyDisplay ( myDisplay )
```

See Also
--------
