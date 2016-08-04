This function creates a new GUI memo. This is a multiline edit box in which the user can input text.

Syntax
------

``` lua
gui-memo guiCreateMemo ( float x, float y, float width, float height, string text, bool relative, [element parent = nil] )
```

### Required Arguments

[frame|Example GUI memo.](/Image:Gui-memo.png.md "wikilink")

-   **x:** A float of the 2D x position of the GUI memo on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI memo on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI memo. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI memo. This is affected by the *relative* argument.
-   **text:** A string of the text that will be displayed by default in the memo.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the GUI memo is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns a gui-memo element of the created memo if it was successfully created, false otherwise.

Example
-------

``` lua
function cMemoFPlayer()
Window = guiCreateWindow(0.3664,0.2764,0.3508,0.3477,"GUI Window",true)
      guiCreateMemo(17,79,414,246,"",false,Window)
end
addEventHandler("onClientResourceStart", resourceRoot, cMemoFPlayer)
```

See Also
--------
