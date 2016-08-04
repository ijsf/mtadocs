This event is triggered when the local client resizes a GUI element.

Parameters
----------

*None*

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the GUI element that was resized.

Example
-------

This example will output the type of GUI element that the client has resized, to the chatbox.

``` lua
addEventHandler("onClientGUISize",guiRoot,function()
    outputChatBox("You have resized a "..getElementType(source)..".",255,255,0)
end)
```

See Also
--------

### GUI events

### Client event functions
