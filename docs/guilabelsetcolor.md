This function allows you to set the color of a GUI label.

Syntax
------

``` lua
bool guiLabelSetColor ( element theElement, int red, int green, int blue )
```

### Required Arguments

-   **theElement:** The label to be changed.
-   **red:** An integer specifying the amount of red (0 to 255).
-   **green:** An integer specifying the amount of green (0 to 255).
-   **blue:** An integer specifying the amount of blue (0 to 255).

### Returns

Returns *true* if the the color of the gui label was successfully changed, *false* otherwise.

Example
-------

This example creates a label with text “Hello World!” and sets it to a random color.

``` lua
local myLabel = guiCreateLabel ( 0.45, 0.48, 0.2, 0.5, "Hello world", true )
guiLabelSetColor ( myLabel, math.random(0, 255), math.random(0, 255), math.random(0, 255) )
```

See Also
--------
