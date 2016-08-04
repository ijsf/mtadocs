This function is used to get the current font that is used to draw text in GUI elements.

Syntax
------

``` lua
string, element guiGetFont ( element guiElement )
```

### Required Arguments

-   **guiElement:** element you wish to get the font of.

### Returns

-   **string** A string containing the name of the element's current font, or false if the gui element passed to the function is invalid.
-   '''element ''' The custom [GUI font](/GUI_font.md "wikilink") that is used, or nil otherwise

Example
-------

This example sets and gets the font of a pre-made gui element and outputs it to chat box.

``` lua
-- We create a dummy gui label to get text of
local dummyGUIElement = guiCreateLabel ( 0.45, 0.48, 0.10, 0.04, "Hello world", true )
guiSetFont ( dummyGUIElement, "sa-gothic" )
-- Output the font of the label to chat box
outputChatBox ( "Font used in the GUI label: " .. guiGetFont ( dummyGuiElement ) )
```

See Also
--------

[ru:guiGetFont](/ru:guiGetFont.md "wikilink")
