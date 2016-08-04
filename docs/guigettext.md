This function is used to get the text of GUI elements like edit boxes, labels, buttons etc.

Syntax
------

``` lua
string guiGetText ( element guiElement )
```

### Required Arguments

-   **guiElement:** element you wish to get text of.

### Returns

Returns a string containing the requested element's text, or false if the gui element passed to the function is invalid.

Example
-------

This example gets the text of a pre-made gui element and outputs it to chat box.

``` lua
-- We create a dummy gui label to get text of
local dummyGUIElement = guiCreateLabel ( 0.45, 0.48, 0.10, 0.04, "Hello world", true )
-- Output the text of the label to chat box
outputChatBox ( "Text in the GUI label: " .. guiGetText ( dummyGUIElement ) )
```

See Also
--------
