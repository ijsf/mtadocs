This event is triggered each time the user scrolls his mouse scroll on top of a GUI element.

Parameters
----------

``` lua
int upOrDown
```

-   **upOrDown**: An integer representing whether the scroll was scrolled up or down. This can be either **1** (mouse was scrolled up) or **-1** (mouse was scrolled down).

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the GUI element on which the mouse scroll was scrolled.

Example
-------

The example tells player in which direction wheel was scrolled (UP or DOWN) and also the type of the GUI element that wheel was scrolled on.

``` lua
addEventHandler( "onClientMouseWheel", root,
    function ( up_down )
        outputChatBox( "You scrolled mouse wheel " .. ( up_down == 1 and "UP" or "DOWN" ) .. " on " .. getElementType( source ) )
    end
)
```

[pl:onClientMouseWheel](/docs/pl:onclientmousewheel.md "wikilink")

See Also
--------

### GUI events

### Client event functions
