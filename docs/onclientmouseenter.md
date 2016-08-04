This event is fired when the user moves the mouse over a GUI element.

Parameters
----------

``` lua
int absoluteX, int absoluteY, element leftGUI
```

-   **absoluteX**: the X position of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY**: the Y position of the mouse cursor, in pixels, measured from the top of the screen.
-   **leftGUI**: the gui element that was switched from, or nil if it doesn't exist

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the GUI element that was pointed at.

Example
-------

This example shows a message when you move over a GUI element.

``` lua
addEventHandler( "onClientMouseEnter", getRootElement(), 
    function(aX, aY)
        outputChatBox( "You're pointing at a GUI element at ("..tostring(aX)..", "..tostring(aY)..")")
    end
)
```

[pl:onClientMouseEnter](/docs/pl:onClientMouseEnter.md "wikilink")

See Also
--------

### GUI events

### Client event functions
