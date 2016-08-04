This function is for creating a new dxGUI button.

Syntax
------

``` lua
element dxCreateButton( float x, float y, float width, float height, string text,[element parent = nil, int color, string font, string theme] )
```

### Required Arguments

-   **x:** A float of the 2D x position of the dxGUI window on a player's screen.
-   **y:** A float of the 2D y position of the dxGUI window on a player's screen.
-   **width:** A float of the width of the dxGUI window.
-   **height:** A float of the height of the dxGUI window.
-   **text:** A string of the text that will be displayed in the button.
-   **parent:** This is the parent that the gui button is attached to.
-   **color:** This the color of dxGUI: tocolor(255,255,255,255).
-   **font:** This the font text of dxGUI titleBarText: “default-bold”.
-   **theme:** This the theme of dxGUI: “Lighter Black”,“Lighter Blue”,“Orange” in themes.xml you can add more.

### Returns

Returns a dxgui element of the created button if it was successfully created, false otherwise.

Example
-------

**Example 1:** This example creates a button.

``` lua
exports.dxGUI_v1:dxCreateButton(0,0,250,300,"Hello!",tocolor(255,0,0,255),"default-bold","Orange")
```
