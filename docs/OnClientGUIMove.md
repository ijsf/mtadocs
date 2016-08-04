This event is triggered each time the user moves a GUI element.

Parameters
----------

*None*

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the GUI element which was moved.

Example
-------

This example would output to the chatbox what the player moved.

``` lua
addEventHandler("onClientGUIMove",guiRoot,function()
    outputChatBox("You have moved :"..getElementType(source))
end)
```

See Also
--------

### GUI events

### Client event functions
