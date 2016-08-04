This function creates a [radio button](/docs/Element/GUI/Radio_button.md "wikilink").

Syntax
------

``` lua
element guiCreateRadioButton ( float x, float y, float width, float height, string text, bool relative, [element parent = nil] )
```

### Required Arguments

[frame|Example GUI radio buttons.](/docs/Image:gui-radiobutton.png.md "wikilink")

-   **x:** A float of the 2D x position of the radio button on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the radio button on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the text field next to the radio button. This is affected by the *relative* argument.
-   **height:** A float of the height of the text field next to the radio button. This is affected by the *relative* argument.
-   **text:** The text to be displayed next to the radio button.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the radio button is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

*NOTE:* All radio buttons become grouped together with their parent item. Only ONE radio button per group/parent will be able to be selected at the same time.

### Returns

Returns [element](/docs/element.md "wikilink") of the radio button if it was created succesfully, *false* otherwise.

Example
-------

This example creates a radio button then checks if one is selected and if it is, then it's output the title and sets the next radio button selected. (TESTED!)

``` lua
hi = guiCreateRadioButton(243,204,36,16,"Hi",false)
guiRadioButtonSetSelected(hi,true)
bye = guiCreateRadioButton(243,224,41,16,"Bye",false)

if(guiRadioButtonGetSelected(hi))then
    outputChatBox("Hi "..getPlayerName(localPlayer))
    guiRadioButtonSetSelected(bye,true)
else
    outputChatBox("Bye "..getPlayerName(localPlayer))
    guiRadioButtonSetSelected(hi,true)
end
```

See Also
--------
