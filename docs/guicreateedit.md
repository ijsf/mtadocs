[frame|Example GUI edit field.](/docs/Image:Gui-edit.png.md "wikilink")

<table>
<tr>
<td valign=top height=80>
This function is for creating a new GUI edit box. This is a text box in which the user can input text. Edit boxes only allow a single line of text. If you want to allow multiple lines of text create a memo box using [guiCreateMemo](/docs/guiCreateMemo.md "wikilink").

</td>
</tr>
</table>
Syntax
------

``` lua
element guiCreateEdit ( float x, float y, float width, float height, string text, bool relative, [element parent = nil] )
```

### Required Arguments

-   **x:** A float of the 2D x position of the GUI edit box on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI edit box on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI edit box. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI edit box. This is affected by the *relative* argument.
-   **text:** A string of the text that will be displayed by default in the edit box.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the GUI edit box is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns a gui-edit element of the created edit box if it was successfully created, false otherwise.

Example
-------

This example creates an edit box alongside an “Output!” button. When the button is clicked, it will output the message in the edit box into the Chat Box.

``` lua
--create our button
button = guiCreateButton( 0.7, 0.1, 0.2, 0.1, "OK", true )
--Create an edit box and define it as "editBox".
editBox = guiCreateEdit( 0.3, 0.1, 0.4, 0.1, "", true )
guiEditSetMaxLength ( editBox, 128 ) --the max chatbox length is 128, so force this

--setup our function to output the message to the chatbox
function outputEditBox ()
        local text = guiGetText ( editBox )--get the text from the edit box
        outputChatBox ( text ) --output that text
end
addEventHandler ( "onClientGUIClick", button, outputEditBox )
```

This example creates an edit box and sets the input focus so the player does not have to click before typing:

``` lua
local editBox = guiCreateEdit( 0.3, 0.1, 0.4, 0.1, "", true )
guiBringToFront( editBox )
guiEditSetCaretIndex( editBox, 1 )
```

See Also
--------

[ru:guiCreateEdit](/docs/ru:guiCreateEdit.md "wikilink")
