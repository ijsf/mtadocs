This event is fired when the user moves the mouse away from a GUI element.

Parameters
----------

``` lua
int absoluteX, int absoluteY, element enteredGUI
```

-   **absoluteX**: the X position of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY**: the Y position of the mouse cursor, in pixels, measured from the top of the screen.
-   **enteredGUI**: is the GUI element that was switched from, or nil if it doesn't exist

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the GUI element that the mouse was moved from.

Example
-------

This example shows a message when you move the mouse away from a GUI element.

``` lua
addEventHandler("onClientMouseLeave", getRootElement(), function(aX, aY)
    outputChatBox("You're no longer pointing at a GUI element at (" .. tostring(aX) .. ", " .. tostring(aY) .. ")")
end)
```

[pl:onClientMouseLeave](/docs/pl:onclientmouseleave.md "wikilink")

See Also
--------

### GUI events

### Client event functions
