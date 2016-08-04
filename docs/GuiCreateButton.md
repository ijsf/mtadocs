This function allows creation of a GUI Button, which is a clickable item as part of GUI.

Syntax
------

``` lua
element guiCreateButton ( float x, float y, float width, float height, string text, bool relative, [ element parent = nil ] )
```

### Required Arguments

[thumb|GUI Test Button](/docs/Image:Button.png.md "wikilink")

-   **x:** A float of the 2D x position of the GUI button on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI button on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI button. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI button. This is affected by the *relative* argument.
-   **text:** A string of the text that will be displayed as a label on the button.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all *x, y, width* and *height* floats must be between 0 and 1, representing sizes relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the gui button is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns an [element](/docs/element.md "wikilink") of the created [button](/Element/GUI/Button.md "wikilink") if it was successfully created, false otherwise.

Example
-------

This example creates an edit box alongside an “Output!” button. When the button is clicked, it will output the message in the edit box into the Chat Box.

``` lua
--create our button
button = guiCreateButton( 0.7, 0.1, 0.2, 0.1, "Output!", true )
--Create an edit box and define it as "editBox".
editBox = guiCreateEdit( 0.3, 0.1, 0.4, 0.1, "Type your message here!", true )
-- and attach our button to the outputEditBox function
addEventHandler ( "onClientGUIClick", editBox, outputEditBox )
guiEditSetMaxLength ( editBox, 128 ) --the max chatbox length is 128, so force this

--setup our function to output the message to the chatbox
function outputEditBox ()
        local text = guiGetText ( editBox )--get the text from the edit box
        outputChatBox ( text ) --output that text
end
addEventHandler ( "onClientGUIClick", button, outputEditBox )
```

See Also
--------

[ru:guiCreateButton](/docs/ru:guiCreateButton.md "wikilink")
