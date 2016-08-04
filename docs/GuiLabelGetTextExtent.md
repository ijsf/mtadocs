This function returns the extent, or width, of the current text inside a GUI text label.

Syntax
------

``` lua
float guiLabelGetTextExtent ( element theLabel )
```

### Required Arguments

-   **theLabel:** The text label to get the text extent from.

### Returns

Returns the absolute width of the current text inside the text label if the function is successful, *false* otherwise.

Example
-------

This example creates a window, a text label, gets the text extent and font height, and sets the text label size according to these values.

``` lua
-- create the window (the container for our label)
local myWindow = guiCreateWindow ( 0, 0, 0.5, 0.4, "Information", true )

-- create the label
local myLabel = guiCreateLabel ( 10, 10, 0, 0, "This is my text container", false, myWindow )

-- get the (absolute) text extent and font height, and use these to size the label
guiSetSize ( myLabel, guiLabelGetTextExtent ( myLabel ), guiLabelGetFontHeight ( myLabel ), false )
```

See Also
--------
