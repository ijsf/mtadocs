<pageclass class="client" subcaption="GUI Class method"></pageclass>

This function creates a [CheckBox](/Element/GUI/Checkbox.md "wikilink") object.

Syntax
------

``` lua
checkboxObject CheckBox:Create ( float x, float y, float width, float height, string text, bool selected, [ bool relative = false, element parent = nil] )
```

### Required Arguments

-   **x:** A float of the 2D x position of the checkbox on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the checkbox on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the text field next to the checkbox. This is affected by the *relative* argument.
-   **height:** A float of the height of the text field next to the checkbox. This is affected by the *relative* argument.
-   **text:** The text to be displayed next to the checkbox.
-   **selected:** A boolean representing whether the checkbox created should be selected by default.

### Optional Arguments

-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent. Default value is **false**
-   **parent:** This is the parent that the checkbox is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

-   **checkboxObject** if it was created succesfully
-   **false** otherwise.

Example
-------

This example does...

``` lua
```

See Also
--------

[Back to GUI Classes page](/GUI_Classes.md "wikilink")
