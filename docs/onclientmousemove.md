This event is triggered each time the user moves the mouse on top of a GUI element.

Parameters
----------

``` lua
int absoluteX, int absoluteY
```

-   **absoluteX**: the X position of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY**: the Y position of the mouse cursor, in pixels, measured from the top of the screen.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the GUI element on which the mouse was moved.

Example
-------

This example creates a text label at the bottom of the screen that tells player the position of mouse when moved on top of a “TEST WINDOW” (the gui element).

``` lua
addEventHandler( "onClientResourceStart", getResourceRootElement( ),
    function ( )
        guiCreateWindow( 10, 200, 200, 150, "TEST WINDOW", false );
        textLabel = guiCreateLabel( 0, .9, 1, .1, "", true );
        guiLabelSetHorizontalAlign( textLabel, "center" );
    end
);

addEventHandler( "onClientMouseMove", getRootElement( ),
    function ( x, y )
        if source then
            if not guiGetVisible( textLabel ) then guiSetVisible( textLabel, true ) end
            guiSetText( textLabel, "X: " .. tostring( x ) .. ";  Y: ".. tostring( y ) )
        else
            guiSetVisible( textLabel, false );
        end
    end
)
```

[pl:onClientMouseMove](/docs/pl:onclientmousemove.md "wikilink")

See Also
--------

### GUI events

### Client event functions
