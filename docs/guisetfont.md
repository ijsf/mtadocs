This function sets the font of a [GUI element](/docs/gui_widgets.md "wikilink") to be used when drawing text.

Syntax
------

``` lua
bool guiSetFont ( element guiElement, mixed font )
```

### Required Arguments

-   **guiElement:** The GUI element you wish to change the font of
-   **font:** Either a custom [GUI font](/docs/gui_font.md "wikilink") element or the name of a built-in GUI font. See [Standard GUI Font Names](/docs/standard_gui_font_names.md "wikilink")

### Returns

Returns *true* if the font has been successfully set on the gui element, *false* otherwise.

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
