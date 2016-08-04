This event is fired when a memo or an editbox has changed (either by the user or by [guiSetText](/guiSetText.md "wikilink")).

Parameters
----------

``` lua
element theElement
```

-   **theElement**: The element which was changed.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the element which was changed.

Example
-------

This example creates an editbox and prints a message when it has changed

``` lua
editBox = guiCreateEdit(0.3,0.1,0.4,0.1,"",true)
addEventHandler("onClientGUIChanged", editBox, function(element) 
   outputChatBox("The box now reads: " .. guiGetText(element))
end)
```

Or

``` lua
editBox = guiCreateEdit(0.3,0.1,0.4,0.1,"",true)
addEventHandler("onClientGUIChanged", editBox, function() 
   outputChatBox("The box now reads: " .. guiGetText(source))
end)
```

[pl:onClientGUIChanged](/pl:onClientGUIChanged.md "wikilink")

See Also
--------

### GUI events

### Client event functions
