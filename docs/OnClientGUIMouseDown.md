This event is fired when the user clicks certain mouse button on a GUI element.

Parameters
----------

``` lua
string button, int absoluteX, int absoluteY
```

-   **button:** the name of the mouse button that the GUI element was clicked with, can be *left*, *right*, or *middle*.
-   **absoluteX:** the X position of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY:** the Y position of the mouse cursor, in pixels, measured from the top of the screen.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the GUI element that was clicked.

Example
-------

This example show how to add very basic *click'n'drag* feature for GUI elements (only for those which parent element is gui-root)

``` lua

addEventHandler( "onClientGUIMouseDown", getRootElement( ),
    function ( btn, x, y )
        if btn == "left" then
            clickedElement = source; -- store the clicked element in a global variable
            local elementPos = { guiGetPosition( source, false ) };
            offsetPos = { x - elementPos[ 1 ], y - elementPos[ 2 ] }; -- get the offset position
        end
    end
);

addEventHandler( "onClientGUIMouseUp", getRootElement( ),
    function ( btn, x, y )
        if btn == "left" then
            clickedElement = nil;
        end
    end
);

addEventHandler( "onClientCursorMove", getRootElement( ),
    function ( _, _, x, y )
        if clickedElement then
            guiSetPosition( clickedElement, x - offsetPos[ 1 ], y - offsetPos[ 2 ], false );
        end
    end
);
```

See Also
--------

### GUI events

### Client event functions
