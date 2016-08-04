This event is triggered when enter is pressed on an editbox.

Parameters
----------

``` lua
element editBox
```

-   **editBox**: The editbox which had focus.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the editbox which enter was pressed on.

Example
-------

This example creates an editbox and prints a message when enter is pressed.

``` lua
editBox = guiCreateEdit ( 0.3, 0.1, 0.4, 0.1, "", true )
addEventHandler( "onClientGUIAccepted", editBox,
    function( theElement ) 
        outputChatBox( guiGetText( theElement ) )
    end
)
```

[pl:onClientGUIAccepted](/docs/pl:onClientGUIAccepted.md "wikilink")

See Also
--------

### GUI events

### Client event functions
