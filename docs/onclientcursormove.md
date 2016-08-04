This event is called by the root element whenever the cursor is moved over the screen, by the player. It returns information about the world coordinates as well as the screen coordinates of where the player moved the cursor.

The difference between this event and [onClientMouseMove](/docs/onclientmousemove.md "wikilink"), is that the latter is actually called by GUI elements. This is to prevent double calling of onClientCursorMove, as onClientCursorMove is always called.

Parameters
----------

``` lua
float cursorX, float cursorY, int absoluteX, int absoluteY, float worldX, float worldY, float worldZ
```

-   **cursorX:** the relative X coordinate of the mouse cursor. 0 = left side of the screen, 1 = right side.
-   **cursorY:** the relative Y coordinate of the mouse cursor. 0 = top of the screen, 1 = bottom.
-   **absoluteX:** the X coordinate of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY:** the Y coordinate of the mouse cursor, in pixels, measured from the top of the screen.
-   **worldX, worldY, worldZ:** the 3D in-game world coordinates that the cursor is pointing at.

Source
------

The source of this event is the root element.

Example
-------

This example creates a text label at the bottom of the screen which displays the mouse position in pixels.

``` lua
addEventHandler( "onClientResourceStart", getResourceRootElement( ),
    function ( )
        textLabel = guiCreateLabel( 0, .9, 1, .1, "X: -;  Y: -", true );
        guiLabelSetHorizontalAlign( textLabel, "center" );
    end
);

addEventHandler( "onClientCursorMove", getRootElement( ),
    function ( _, _, x, y )
        guiSetText( textLabel, "X: " .. tostring( x ) .. ";  Y: ".. tostring( y ) )
    end
);
```

[pl:onClientCursorMove](/docs/pl:onclientcursormove.md "wikilink")

See Also
--------

### GUI events

### Client event functions
