This event is fired when a GUI scrollbar is scrolled.

Parameters
----------

``` lua
element Scrolled
```

-   **Scrolled**: The scrollbar element that was scrolled

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the scrollbar element that got scrolled.

Example
-------

This example outputs a message with the new scroll position when a scrollbar is scrolled.

``` lua
function OnScroll(Scrolled)
    outputChatBox("The new scroll position is "..guiScrollBarGetScrollPosition(Scrolled))
end
addEventHandler("onClientGUIScroll",getRootElement(),OnScroll)
```

[pl:onClientGUIScroll](/pl:onClientGUIScroll.md "wikilink")

See Also
--------

### GUI events

### Client event functions
